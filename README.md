# [PhoneGap Blog](http://phonegap.com/blog) [![Travis Build Status](https://travis-ci.org/phonegap/blog.svg?branch=gh-pages)](https://travis-ci.org/phonegap/blog)

This is a fairly vanilla [Jekyll](http://jekyllrb.com)/[GitHub Pages](https://pages.github.com/) site. It has been optimized for improved page loading speed; see [this article](http://garthdb.com/writings/i-am-a-jekyll-god/) for a full description.

## Setup

Install [`rvm`](https://rvm.io/) to manage Ruby versions:

```bash
$ \curl -sSL https://get.rvm.io | bash -s stable
```

Install Ruby:

```bash
$ rvm install 2.1.5
$ rvm use 2.1.5 --default
$ ruby -v
ruby 2.1.5
```

Install the Ruby Bundler:

```bash
$ gem install bundler
```

Clone this repository:

```bash
$ git clone https://github.com/phonegap/blog.git
$ cd blog/
```

Install the Ruby dependencies for phonegap.com:

```bash
$ bundle install
```

## Running Locally

**Build and watch everything _except the blog_:**

```bash
$ rake watch
```

Then open a browser to `http://localhost:4000/blog/`.

**Build and watch everything _including the blog_:**

```bash
$ jekyll serve --incremental
```

Then open a browser to `http://localhost:4000/blog/`.

## Writing Blog Posts

* To write a post, commit a markdown file to the `_posts/blog/` directory.
* You can use the [post template](https://github.com/phonegap/blog/blob/gh-pages/_post.txt) as a starting point.
  * Optionally you can also use a Rake task to create the new post file locally. Install Ruby and Rake as mentioned above in the "Setup" section. Run `$ rake post["Put the Post Title Here"]`
* Name the file with the date first, followed by a url friendly version of the title. Example: `2016-02-24-phonegap-desktop-app-0.2.2.md`
* Tag pages have to be set up manually; do your best to use existing ones, if you need to set up a new one, setup a new tag page in the `/blog/tags` using the [tag template](https://github.com/phonegap/blog/blob/master/blog/tags/_template.html)
* Use [markdown](https://daringfireball.net/projects/markdown/) for simple formatting. It is converted to html using [Kramdown](http://kramdown.gettalong.org/)
* HTML is also acceptable, just use the `.html` extension on the filename.
* To keep videos and images responsive please don't add the `width` property. If images are too large you can add the `max-width` style: `<img src="/uploads/blog/2016-02/Browser.jpg" alt="Browser" style="max-width: 400px;"/>`
* To include images, add them to `/uploads/blog/[4 digit year]-[2 digit month]`. If the directory you need for the month isn't there, feel free to add it. To include the image in the post just use the same directory structure: `![Browser](/uploads/blog/2016-02/Browser.jpg)`.
* Kramdown is using [GitHub Flavored Markdown](https://help.github.com/articles/working-with-advanced-formatting/). The easiest way to add code snippets is to using [triple backticks](https://help.github.com/articles/creating-and-highlighting-code-blocks/#fenced-code-blocks); you can also define the language for better [syntax highlighting](https://help.github.com/articles/creating-and-highlighting-code-blocks/#syntax-highlighting). For a full list of languages [here](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml).
* You can preview the post locally using the setup and commands mentioned above in the [Setup](https://github.com/phonegap/blog/#setup) section.
* If you have write access to this repo and you feel comfortable with the blog post, feel free to commit to master.
* If you **don't** have write access to this repo, or you would like a review, please make a [pull-request](https://help.github.com/articles/using-pull-requests/).


## Test Locally

The site is using [Travis CI](https://travis-ci.org/phonegap/blog) and [HTML Proofer](https://github.com/gjtorikian/html-proofer) to check the html and referenced urls. Before you make a pull request it's a good idea to run the tests locally first.

Just run the command:

```bash
$ rake test
```

The output should be something like:

```bash
Running ["ScriptCheck", "LinkCheck", "ImageCheck"] checks on ./_site on *.html...


Checking 7 external links...
Ran on 3 files!


HTML-Proofer finished successfully.
```

If it finds any errors be sure to fix them before making the pull-request.
