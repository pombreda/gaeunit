
---

## New Developer Wanted ##

As a loyal GAEUnit user, you may have noticed that the project has not yet been updated for a while. I have to apologize for this situation. But as the main developer of GAEUnit, I am afraid that it is not able to be changed in near future.

I created this project 2 years ago as a community project. Now I hope this project can be continuously pushed forward by the power of community. If you want to join us and contribute your own strength, please send email to george.z.lei (at) gmail (dot) com.


---


## GAEUnit 2.0 alpha for Django is released, please download and follow the instruction. ##

GAEUnit is a unit test framework that helps to automate testing of your Google App Engine application. With a single configuration change (it can be completed within 30 seconds), your unit tests can be run in the real GAE app server environment using a web browser.

GAEUnit is simple. It contains only one file: gaeunit.py. Just copy that file into your application directory and add the test URL to app.yaml.

**Usage**

1. Configure the environment:
  * Copy `gaeunit.py` to the project directory.
  * Add the following 2 lines to `app.yaml`:

```
- url: /test.*
  script: gaeunit.py
```


2. Write your test case scripts in Python modules, each containing `unittest.TestCase` subclasses, in the 'test' directory and launch `dev_appserver.py`

3. Browse to the following URL (change the port if necessary):

```
http://localhost:8080/test
```

Your test results will be displayed in the browser:

http://gaeunit.googlecode.com/files/gaeuni_1.1.0_screenshot.JPG

If you wish to run a single module, execute it like this:

```
http://localhost:8080/test?name=my_test_module
```

You can also specify a single test class, like `name=my_test_module.MyTestCase` or even a single test method, like `name=my_test_module.MyTestCase.test_stuff`

See [FeatureCandidates](FeatureCandidates.md) for a list of potential upcoming features.

Please let us know if you have interesting ideas or specific requirements for GAEUnit.  Use the comments on the FeatureCandidates page, or use the Issues tab above.