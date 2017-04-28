# == Dependencies ==============================================================

require 'rake'
require 'yaml'
require 'fileutils'
require 'rbconfig'
require 'html-proofer'
require "csv"

# == Configuration =============================================================

# Set "rake watch" as default task
task :default => :watch

# Load the configuration file
CONFIG = YAML.load_file("_config.yml")

# Get and parse the date
DATE = Time.now.strftime("%Y-%m-%d")

# Directories
POSTS = "_posts/"
RESOURCES = "resources/_posts/"
DRAFTS = "_drafts"

# == Helpers ===================================================================

# Execute a system command
def execute(command)
  system "#{command}"
end

# Check the title
def check_title(title)
  if title.nil? or title.empty?
    raise "Please add a title to your file."
  end
end

# Transform the filename and date to a slug
def transform_to_slug(title, extension)
  characters = /("|'|!|\?|:|\s\z)/
  whitespace = /\s/
  "#{title.gsub(characters,"").gsub(whitespace,"-").downcase}.#{extension}"
end

# Read the template file
def read_file(template)
  File.read(template)
end

# Save the file with the title in the YAML front matter
def write_file(content, title, directory, filename)
  parsed_content = "#{content.sub("title:", "title: \"#{title}\"")}"
  File.write("#{directory}/#{filename}", parsed_content)
  puts "#{filename} was created in '#{directory}'."
end

# Create the file with the slug and open the default editor
def create_file(directory, filename, content, title, editor)
  if File.exists?("#{directory}/#{filename}")
    raise "The file already exists."
  else
    write_file(content, title, directory, filename)
    if editor && !editor.nil?
      sleep 1
      execute("#{editor} #{directory}/#{filename}")
    end
  end
end

# Get the "open" command
def open_command
  if RbConfig::CONFIG["host_os"] =~ /mswin|mingw/
    "start"
  elsif RbConfig::CONFIG["host_os"] =~ /darwin/
    "open"
  else
    "xdg-open"
  end
end

def parse_posts
  Dir.chdir POSTS
  data = []
  files = Rake::FileList["**/*.md", "**/*.markdown", "**/*.html"]
  files.exclude("README.md")
  for file in files
    content = File.read("#{File.dirname(__FILE__)}/#{POSTS}#{file}")
    if content.include? "---"
      yaml_data = content.split('---')[1]
      yaml_data = YAML.load(yaml_data)
      data.push(yaml_data)
    end
  end
  return data
end

# == Tasks =====================================================================

# rake tags
desc "Generate a page for each tag"
task :tags do
  posts = parse_posts()
  tags = []
  for post in posts
    tags_temp = post["tags"]
    if tags_temp.respond_to?('each')
      tags.push(*tags_temp)
    end
  end
  tags = tags.uniq - ["", nil]
  for tag in tags
    content = File.read("#{File.dirname(__FILE__)}/tags/_template.html")
    parsed_content = content.gsub!("{tag}", tag)
    slug = tag.gsub(" ", "-").downcase
    parsed_content = content.gsub("{slug}", slug)
    directory = "#{File.dirname(__FILE__)}/tags"
    File.write("#{directory}/#{slug}.html", parsed_content)
    puts "#{slug}.html"
  end
end

# rake authors
desc "Generate a page for each author"
task :authors do
  posts = parse_posts()
  authors = []
  for post in posts
    authors.push(post["author"])
  end
  authors = authors.uniq - ["", nil]
  for author in authors
    content = File.read("#{File.dirname(__FILE__)}/authors/_template.html")
    parsed_content = content.gsub!("{author}", author)
    slug = author.gsub(/\W/, "-").downcase.gsub(/---*/, "-")
    parsed_content = content.gsub("{slug}", slug)
    directory = "#{File.dirname(__FILE__)}/authors"
    File.write("#{directory}/#{slug}.html", parsed_content)
    puts "#{slug}.html"
  end
end

# rake post["Title"]
desc "Create a post in _posts/"
task :post, :title do |t, args|
  title = args[:title]
  template = CONFIG["post"]["template"]
  extension = CONFIG["post"]["extension"]
  editor = CONFIG["editor"]
  check_title(title)
  filename = "#{DATE}-#{transform_to_slug(title, extension)}"
  content = read_file(template)
  create_file(POSTS, filename, content, title, editor)
end

# rake draft["Title"]
desc "Create a post in _drafts"
task :draft, :title do |t, args|
  title = args[:title]
  template = CONFIG["post"]["template"]
  extension = CONFIG["post"]["extension"]
  editor = CONFIG["editor"]
  check_title(title)
  filename = transform_to_slug(title, extension)
  content = read_file(template)
  create_file(DRAFTS, filename, content, title, editor)
end

# rake publish
desc "Move a post from _drafts to _posts"
task :publish do
  extension = CONFIG["post"]["extension"]
  files = Dir["#{DRAFTS}/*.#{extension}"]
  files.each_with_index do |file, index|
    puts "#{index + 1}: #{file}".sub("#{DRAFTS}/", "")
  end
  print "> "
  number = $stdin.gets
  if number =~ /\D/
    filename = files[number.to_i - 1].sub("#{DRAFTS}/", "")
    FileUtils.mv("#{DRAFTS}/#{filename}", "#{POSTS}/#{DATE}-#{filename}")
    puts "#{filename} was moved to '#{POSTS}'."
  else
    puts "Please choose a draft by the assigned number."
  end
end

# rake build
desc "Build the site"
task :build do
  execute("jekyll build")
end

# rake watch
# rake watch[number]
# rake watch["drafts"]
desc "Serve and watch the site (with post limit or drafts)"
task :watch, :option do |t, args|
  option = args[:option]
  if option.nil? or option.empty?
    execute("JEKYLL_ENV=local-test bundle exec jekyll serve --watch --incremental")
  else
    if option == "drafts"
      execute("JEKYLL_ENV=local-test bundle exec jekyll serve --watch --drafts --incremental")
    else
      execute("JEKYLL_ENV=local-test bundle exec jekyll serve --watch --limit_posts #{option} --incremental")
    end
  end
end

# rake preview
desc "Launch a preview of the site in the browser"
task :preview do
  port = CONFIG["port"]
  if port.nil? or port.empty?
    port = 4000
  end
  Thread.new do
    puts "Launching browser for preview..."
    sleep 1
    execute("#{open_command} http://localhost:#{port}/")
  end
  Rake::Task[:watch].invoke
end


desc "Delete older files from _site-test before running html proofer"
task :deleteOldFiles do
  sh 'rm -rf ./_site-test/blog/2008/ ./_site-test/blog/2009/ ./_site-test/blog/2010/ ./_site-test/blog/2011/ ./_site-test/blog/2012/ ./_site-test/blog/2013/ ./_site-test/blog/2014/ ./_site-test/blog/tag/phonegap-network/index.html'
end

desc "Convert HTML Proof log to CSV"
task :convertLog do
  filePath = './tmp/.htmlproofer/cache.log'
  if File.exists? filePath
    file = File.read(filePath)
    data_hash = JSON.parse(file)
    CSV.open("./tmp/.htmlproofer/log.csv", "wb") do |csv|
      csv << ['Url','File','Status','Message']
      data_hash.each do |attr_name, attr_value|
        if attr_value['status'] != 200
          data_array = [attr_name, attr_value['filenames'].join(","), attr_value['status'], attr_value['message']]
          csv << data_array
        end
      end
    end
    puts './tmp/.htmlproofer/log.csv' + ' written'
  else
    puts filePath + " not found"
  end
end

# rake test
desc "build and test website"
task :test do
  if !File.exists? "./_site-test"
    sh "JEKYLL_ENV=local-test bundle exec jekyll build --config _config-test.yml"
    Rake::Task[:deleteOldFiles].invoke
  end
  HTMLProofer.check_directory("./_site-test", {
    :check_html => true,
    :empty_alt_ignore => true,
    :http_status_ignore => [0, 403, 999],
    :url_ignore => [
      '/',
      '/about/',
      '/about/faq/',
      '/about/license/',
      '/about/logos/',
      '/about/contact/',
      '/app/',
      '/book/',
      '/event/',
      '/getstarted/',
      '/products/',
      '/tool/',
      'https://phonegap.com/blog/feed.xml',
      '/blog/tag/phonegap-network/',
      /\/blog\/(200\d|201[0-4])\/(\S)*/,
      /http(s)?:\/\/(www.)?linkedin\.com\/in\/([-a-zA-Z0-9@:%_\+.~#?&\/=]*)/
    ],
    :cache => {
      :timeframe => '1d'
    },
    :typhoeus => {
      :followlocation => true,
      :ssl_verifypeer => false,
      :headers => { 'User-Agent' => 'html-proofer' }
    }
  }).run
end
