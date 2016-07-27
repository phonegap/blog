---
author: Garth Braithwaite
title: "Topmarks Performance Benchmarks"
tags:
- News
---
I am in the process of resurrecting [Topcoat](http://topcoat.io). I'm being helped by a few people at Adobe and we are looking at the potential future of the project.

## Performance First

Topcoat has always been driven by performance, so before I spent much time writing new Topcoat code, I needed to get the benchmarks up and running again. The previous performance benchmarks used [Chromium's Telemetry tools](https://www.chromium.org/developers/telemetry/run_locally) which allowed us to test the performance of the components in a real world Chrome browser. However, the Telemetry tool is not well documented, and is a bit cumbersome to set up and run.

This return to Topcoat has given me the chance to reexamine the tool and improve the installation and running experience. Since I think the tool would have use outside of the Topcoat ecosystem, I've broken it off as a new project called [Topmarks](https://github.com/Topmarks/topmarks).

## What is Topmarks?

Topmarks is a node package that can be installed and run as a command line, or within other node projects and build processes. It uses the [chrome-remote-interface](https://github.com/cyrus-and/chrome-remote-interface) package to interface with [Chrome's debugger protocol](https://chromedevtools.github.io/debugger-protocol-viewer/tot/) to send commands to the Chrome browser, like opening a page in a new tab and simulating scrolling. While performing the actions, Topmarks can trace the browser's performance and give a report on the visual performance (including framerate, number of large frames, frame breakdown, etc).

## Installing and Running Topmarks

Install Topmarks using npm. To use it as a command line tool, it should be installed globally:

```sh
$ npm install -g topmarks
```

To allow Topmarks to interface with Chrome, the browser has to be started with the remote debugging port. To do this, start it form the command line. If you are using OS X use a command like this:

```sh
$ /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222 --user-data-dir=$TMPDIR/chrome-profiling --no-default-browser-check --bwsi --window-size="800,600" --enable-gpu-benchmarking
```

After Chrome is running with the `--remote-debugging-port` set to `9222`, you can use the `topm` command line tool to run the default tests.

```sh
topm --port 9222 --url http://topcoat.io
```

Using the `--port 9222` is unnecessary since it defaults to 9222, but use `--url` to tell Topmarks what page to test.

Unless specified otherwise, Topmarks will run the default tests: [topmark-loadspeed](https://github.com/Topmarks/topmark-loadspeed) and [topmark-scrollspeed](https://github.com/Topmarks/topmark-scrollspeed). After running the tests, Topmarks will return a report to the command line that looks something like:

```json
[  
  {  
    "plugin":"loadspeed",
    "url":"http://topcoat.io",
    "timestamp":1469611482321,
    "report":1.1176389999964158
  },
  {  
    "plugin":"scrollspeed",
    "url":"http://topcoat.io",
    "timestamp":1469611487694,
    "report":{  
      "averageFrameRate":43.77,
      "totalFrameCount":95,
      "totalLargeFrameCount":10,
      "frameBreakDown":{  
        "idle":"97.9%",
        "other":"1.31%",
        "painting":"0.63%",
        "rendering":"0.07%",
        "scripting":"0.08%",
        "loading":"0%"
      }
    }
  }
]
```

This report can be written to a file using `--output [filename]`, or even append the results to the end of an existing report file using the `--append-output` option.

### Benchmark Tests

In an effort to make it easier to create and run benchmark tests, Topmarks uses a plugin architecture. If you are interested in writting your own Topmarks tests, take a look at the default plugins and let me know if you have any questions.

## What's Next?

Now that the benchmark tests are run using node, I'll be integrating them into the components and running them each time a new build is pushed to github. I'll be releasing the code for the git hooks and front end graphs on the [Topmarks github organization](https://github.com/Topmarks/) as I work on them.
