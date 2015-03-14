# GAEUnit: Google App Engine Unit Test Framework #

**Version 1.2.5**

http://code.google.com/p/gaeunit

Copyright (c) 2008 George Lei and Steven R. Farley.  All rights reserved.

## SUMMARY ##

GAEUnit is a unit test framework that helps to automate testing of your Google App Engine application. With a single configuration (it can be completed within 30 seconds), your unit tests can be run in the real GAE app server environment. The results will be sent to web browser as an HTML web page.

GAEUnit is simple. It contains only one file, gaeunit.py. Just copy that file into your application directory, add the test URL to `app.yaml`, you can start testing your apps for Google App Engine.

## WHAT'S NEW IN 1.2.5 ##

  * Tests are run concurrently; results are updated as each test completes.
  * Source code refactoring.
  * Bug fixes.

## INSTALLATION ##

  1. Copy `gaeunit.py` into your web app root directory (the directory containing `app.yaml`).
  1. Modify `app.yaml` by adding the following mapping below the `handlers:` section:
```
- url: /test.*
  script: gaeunit.py
```

## WRITING TESTS ##

When writing your test code, please follow the Python unit test coding conventions (http://docs.python.org/lib/writing-tests.html). Here are some simple rules:
  * All test modules should be named like `test_xxx.py`. (This is not strictly necessary for GAEUnit.)
  * All test classes must extend `unittest.TestCase`.
  * All test functions name must be in the format of `testXxx()`.

### Default Organization ###

Put your test modules under the `test` directory. The structure of your web app files should look like the following:
```
guestbook/
   |---- app.yaml
   |---- guestbook.py
   |---- another_mod.py
   |---- test/
           |---- test_guestbook.py
           |---- test_another_mod.py
```
By default all modules in the `test` directory will be searched for `TestCase` subclasses.

### Package Organization ###

If you prefer to organize your tests differently, you can save them as packages with the addition of an `_init_.py` file, like this:
```
guestbook/
    |---- app.yaml
    |---- guestbook.py
    |---- another_mod.py
    |---- packaged_tests/
            |---- __init__.py
            |---- test_guestbook.py
            |---- test_another_mod.py
```
`__init__.py` must contain a line like the following which explicitly lists all test modules:
```
__all__ = ['test_guestbook', 'test_another_mod'] 
```
Note that certain options are not available when tests are packaged this way.  For example, you cannot specify the name of a single test class or method to run with the `name` URL parameter.

## RUNNING TESTS ##

  1. Launch `dev_appserver.py` or the App Engine Launcher user interface.
  1. Type `http://localhost:8080/test` into the location bar of your browser. (Change the port if necessary.)  All tests under the `test` directory will be run concurrently.  Test failures and errors will be reported as they occur.

### Options ###

There are a few options for running tests.  These are set using the URL parameters defined below:

#### name ####
Runs a specific test module, class, or method.

Examples:
  * `http://localhost:8080/test?name=test_module`
  * `http://localhost:8080/test?name=test_module.ClassTest`
  * `http://localhost:8080/test?name=test_module.ClassTest.testMethod`

#### package ####
Runs all tests in a package.

Example:
  * `http://localhost:8080/test?package=test_package`

#### format ####
Sets the content type of the test result. The value can be `html` for HTML format (the default) or `plain` for plain text format.

Example:
  * `http://localhost:8080/test?format=plain`