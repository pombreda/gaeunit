These are some of the ideas for the next release of GAEUnit. Please feel free to comment and suggest new features.

**Support for Coverage:**

GAEUnit does not provide support for coverage testing. We could provide support for determining coverage and generating an html report. We will not supply the coverage module with our source and it will be the choice of the users if they want to run GAEUnit with coverage.(coverage can be easily installed from pypi).

**A New Interface:**

The present gaeunit users presently specify the tests to run as URL arguments. Instead, we can have a starting page or a welcome page where users can mention the tests to run. The tests to run can be collected in a text box and whether to run all the tests through a radio button. We can also have options for users to choose if they want to see only the summary of the results such as only the tests which failed. There can also be an option to hide the traceback when the tests are run and just display a clickable line which shows the test which had failed. After the completion of the tests, the user can click on the line and it will expand to display the traceback corresponding to the failed test.