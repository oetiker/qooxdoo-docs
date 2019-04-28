Generator Usage
===============

The generator is a command-line utility which serves as the single entry front-end for all qooxdoo tool chain functions (nearly; there are a few functions that are available through other programs, but these really serve special purposes).

The generator is started to execute various jobs. Those jobs represent the feature set of the tool chain. This page is about how to invoke the generator.

Files and Folder Structure
--------------------------

The qooxdoo SDK has a dedicated `tool` folder that contains all elements that make up the tool chain. The general structure is like this:

    tool
       |- app   -- helper apps
       |- bin   -- stand-alone programs and scripts
       |- data  -- various data files
       |- pylib -- Python modules

The generator is actually the program `tool/bin/generator.py`.

generate.py
-----------

To make it easier to invoke the generator, each library in the SDK (framework, applications, components) contains a `generate.py` script that is really just a proxy for the generator itself. It is also part of each project created by the create-application.py \<pages/getting\_started/helloworld\#create\_your\_application\> wizard. The aim is to hide the actual path to the generator program. You can omit using it if you add *\<QOOXDOO\_PATH\>/tool/bin* to your PATH environment variable.

Command-line Options
--------------------

Since the generator is nearly completely driven by its configuration files, there are rather few command-line options:

    shell> generator.py -h
    Usage: generator.py [options] job,...

    Arguments:
      job,...               a list of jobs (like 'source' or 'copy-files',
                            without the quotes) to run
      x                     use 'x' (or some undefined job name) to get a
                            list of all available jobs from the configuration file

    Options:
      -h, --help            show this help message and exit
      -c CFGFILE, --config=CFGFILE
                            path to configuration file containing job definitions
                            (default: config.json)
      -q, --quiet           quiet output mode (extra quiet)
      -v, --verbose         verbose output mode of job processing
      -w, --config-verbose  verbose output mode of configuration processing
      -l FILENAME, --logfile=FILENAME
                            log file
      -s, --stacktrace      enable stack traces on fatal exceptions
      -m KEY:VAL, --macro=KEY:VAL
                            define/overwrite a global 'let' macro KEY with value
                            VAL
      -I, --no-progress-indicator
                            suppress animated progress indication

The most important options are the path of the config file to use (*-c* option), and the list of jobs to execute. The *-m* option allows Json-type values, scalars like strings and numbers, but also maps *{...}* and lists *[...]* [1].

Configuration Files
-------------------

The single most important way to control the actions of the generator is through specialized configuration files. These files have a [JSON](http://www.json.org) syntax and contain the definitions for the various jobs the generator is supposed to execute. There is a whole section \<generator\_config\> in this manual dedicated to these config files.

Usage Patterns
--------------

As a few quick hints on how you would invoke the generator, here are the most common use cases. All these examples name a single job to run, and rely on the availability of the default config file `config.json` in the current directory:

-   `generate.py source` -- when you just started to create your application and every time you have added new classes to it.
-   `generate.py build` -- when you have completed your application and/or want to create an optimized, deployable version of it.
-   `generate.py api` -- when your application is getting complex and/or you want to have a local version of the standard [Apiviewer](http://api.qooxdoo.org) application that includes the documentation of all of your application classes.
-   `generate.py test` -- when you have created unit test classes for your application and want to run them in the [Testrunner](http://demo.qooxdoo.org/%{version}/testrunner) frame application.

The Helloworld \<pages/getting\_started/helloworld\#helloworld\> tutorial will give the complete steps how to start a project and get going.

Default Jobs
------------

Arguments like `source` or `api`, as shown in the previous section, are so called *jobs* in qooxdoo lingo. If you are working on a skeleton-based application you automatically get a whole list of such pre-defined jobs to work with. For a quick overview, invoke the generator script with an undefined job argument, like

    generate.py X

This gives you a list of all jobs available through your current config file, many of them with a few words of explanation about what they do:

``` {.sourceCode .text}
- api          -- create api doc for the current library
- build        -- create build version of current application
- clean        -- remove local cache and generated .js files (source/build)
- distclean    -- remove the cache and all generated artefacts of this library...
- fix          -- normalize whitespace in .js files of the current library ...
- lint         -- check the source code of the .js files of the current library
- migration    -- migrate the .js files of the current library to the current ...
- pretty       -- pretty-formatting of the source code of the current library
- profiling    -- includer job, to activate profiling
- source       -- create source version of current application
- source-all   -- create source version of current application, with all classes
- test         -- create a test runner app for unit tests of the current library
- test-source          -- create a test runner app for unit tests (source...
- translation          -- create .po files for current library
```

For an exhaustive reference of these default jobs, see the default jobs page \<default\_jobs\_actions\>.

* * * * *

[1] Caveat: The latter two might push you to the brink of your shell's quoting capabilities :-) .