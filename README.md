![](http://cdn2.hubspot.net/hubfs/100006/images/SB_Logo19.png "SeleniumBase")

[![pypi](https://img.shields.io/pypi/v/seleniumbase.svg)](https://pypi.python.org/pypi/seleniumbase) [![Build Status](https://travis-ci.org/seleniumbase/SeleniumBase.svg?branch=master)](https://travis-ci.org/seleniumbase/SeleniumBase) [![GitHub stars](https://img.shields.io/github/stars/seleniumbase/seleniumbase.svg "GitHub stars")](https://github.com/seleniumbase/SeleniumBase/stargazers) [![Python version](https://img.shields.io/badge/python-2.7-22AADD.svg "Python version")](https://docs.python.org/2/) [![MIT License](http://img.shields.io/badge/license-MIT-22BBCC.svg "MIT License")](https://github.com/seleniumbase/SeleniumBase/blob/master/LICENSE) [![Join the chat at https://gitter.im/seleniumbase/SeleniumBase](https://badges.gitter.im/seleniumbase/SeleniumBase.svg)](https://gitter.im/seleniumbase/SeleniumBase?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

**Web Automation Made Simple & Reliable**

![](http://cdn2.hubspot.net/hubfs/100006/images/sb_demo.gif "SeleniumBase")

(Above: Actual demo of [my_first_test.py](https://github.com/seleniumbase/SeleniumBase/blob/master/examples/my_first_test.py) running against [xkcd.com](http://xkcd.com/353/) in Demo Mode, which automatically highlights page elements being acted on.)

#### **Features include:**
* A complete test framework for running GUI tests with Python's nosetests and pytest.
* [A Python library](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/fixtures/base_case.py) for quickly building [reliable WebDriver scripts](https://github.com/seleniumbase/SeleniumBase/blob/master/examples/my_first_test.py).
* [Plugins](https://github.com/seleniumbase/SeleniumBase/tree/master/seleniumbase/plugins) for logging [data and screenshots](https://github.com/seleniumbase/SeleniumBase/tree/master/examples/example_logs) automatically.
* A flexible command line interface [in Pytest](https://github.com/seleniumbase/SeleniumBase/blob/master/conftest.py) and [in Nosetests](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/plugins/selenium_plugin.py) for customizing test runs.
* [A global configuration file](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/config/settings.py) for making SeleniumBase unique to your specific test environment.
* Easy integration with [Selenium Grid](https://github.com/seleniumbase/SeleniumBase/tree/master/integrations/selenium_grid), [MySQL](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/core/testcase_manager.py), [Docker](https://github.com/seleniumbase/SeleniumBase/blob/master/integrations/docker/ReadMe.md), [NodeJS](https://github.com/seleniumbase/SeleniumBase/tree/master/integrations/node_js), [Google Cloud](https://github.com/seleniumbase/SeleniumBase/tree/master/integrations/google_cloud/ReadMe.md), and [Amazon S3](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/plugins/s3_logging_plugin.py).

SeleniumBase makes it easy to automate tedious business tasks. (*To learn about businesses using SeleniumBase, [Click Here](https://github.com/seleniumbase/SeleniumBase/blob/master/help_docs/happy_customers.md).*)

SeleniumBase also includes an automated/manual hybrid solution called **[MasterQA](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/masterqa/ReadMe.md)**, which speeds up manual testing.

### **Part I: Setup Instructions for Mac, Ubuntu, and Windows**

*(**Debian Linux users**: Run [Linuxfile.sh](https://github.com/seleniumbase/SeleniumBase/blob/master/integrations/linux/Linuxfile.sh) to setup your Debian Linux machine.)*

*(**Docker users**: See the [Docker ReadMe](https://github.com/seleniumbase/SeleniumBase/blob/master/integrations/docker/ReadMe.md) to setup your Docker machine.)*


#### **Step 0a:** Setup your Python/pip environment:

* To install ``python``, ``pip``, ``git``, and either ``virtualenv`` or ``virtualenvwrapper``, **[follow these instructions](https://github.com/seleniumbase/SeleniumBase/blob/master/help_docs/requirements_installation.md)**.


#### **Step 0b:** Install web browsers to run automation on:

* Download & install web browsers such as [Chrome](https://www.google.com/chrome/browser/desktop/index.html) (or [Chromium](https://download-chromium.appspot.com/)) and [Firefox](https://www.mozilla.org/firefox/new/).


#### **Step 0c:** Get web drivers for each browser you intend to run automation on:

To run automation on various web browsers, you'll need to download a driver file for each one and place it on your System **[PATH](http://java.com/en/download/help/path.xml)**. On a Mac, ``/usr/local/bin`` is a good spot. On Windows, make sure you set the System Path under Environment Variables to include the location where you placed the driver files:

* For Chrome, get [Chromedriver](https://sites.google.com/a/chromium.org/chromedriver/downloads) on your System Path.

* For Firefox, get [Geckodriver](https://github.com/mozilla/geckodriver/releases) on your System Path.

* For Microsoft Edge, get [Edge Driver (Microsoft WebDriver)](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) on your System Path.

* For Safari, get [Safari Driver](https://github.com/seleniumbase/SeleniumBase/blob/master/help_docs/using_safari_driver.md) on your System Path.

* For PhantomJS headless browser automation, get [PhantomJS](http://phantomjs.org/download.html) on your System Path.

(NOTE: For older versions of Firefox such as 46.0 and earlier, you don't need Geckodriver. The older driver comes prepackaged with Selenium.)

(NOTE: If you don't have access rights to update system variables, you can use the [Anaconda Version of Python 2](https://www.continuum.io/downloads). In that case, place web drivers in ``Anaconda_Installation_Path/Scripts/``)

Mac:

* On a Mac, you can install drivers more easily by using ``brew`` (aka ``homebrew``), but you have to install that first. [Brew installation instructions are here](https://github.com/seleniumbase/SeleniumBase/blob/master/help_docs/requirements_installation.md).

```bash
brew install chromedriver phantomjs
```

* To verify that the web drivers are working, **[follow these instructions](https://github.com/seleniumbase/SeleniumBase/blob/master/help_docs/verify_webdriver.md)**.


#### **Step 1:** Clone SeleniumBase to your local machine

```bash
git clone https://github.com/seleniumbase/SeleniumBase.git
cd SeleniumBase
```

(A Git GUI tool like [SourceTree](http://www.sourcetreeapp.com/) may make things easier.)


#### **Step 2:** Create & activate a virtual environment for SeleniumBase

If you're not sure how to create a virtual environment, **[follow these instructions](https://github.com/seleniumbase/SeleniumBase/blob/master/help_docs/virtualenv_instructions.md)** to learn how.


#### **Step 3:** Install SeleniumBase

Since [SeleniumBase is in Pypi](https://pypi.python.org/pypi/seleniumbase), you can install it like this: (Using ``"sudo"`` may be required.)
```bash
pip install seleniumbase --upgrade
```

You can also customize your local version of SeleniumBase. If you change the Python requirements or make any changes to the SeleniumBase library files, just run the following commands from the SeleniumBase top-level directory for your changes to take effect:

```bash
pip install -r requirements.txt --upgrade
```

```bash
python setup.py install
```

If you wish to use the MySQL functionality with SeleniumBase to store test results and data in the database, you'll need to [follow these instructions](https://github.com/seleniumbase/SeleniumBase/blob/master/help_docs/mysql_installation.md).


#### **Step 4:** Verify that SeleniumBase was successfully installed by running the example test

You can verify the installation of SeleniumBase by running a simple script to perform basic actions such as navigating to a web page, clicking, waiting for page elements to appear, typing in text, scraping text on a page, and verifying text. In most web browsers, you can right-click on a page and select "Inspect Element" to see the CSS selector details that you need to create such a script. With CSS selectors, dots represent class names and pound signs represent IDs.

Here's what the code looks like from the first example script that you'll be running:

```python
from seleniumbase import BaseCase

class MyTestClass(BaseCase):

    def test_basic(self):
        self.open('http://xkcd.com/353/')                       # Opens the url
        self.assert_element('img[alt="Python"]')      # Asserts element on page
        self.click('a[rel="license"]')                 # Clicks element on page
        xkcd_license = self.get_text('center')    # Gets text from page element
        self.assertTrue('reuse any of my drawings' in xkcd_license)
        self.open('http://xkcd.com/1481/')
        image_object = self.find_element('#comic img')    # Returns the element
        caption = image_object.get_attribute('title')  # Gets attr from element
        self.assertTrue('connections to the server' in caption)
        self.click_link_text('Blag')          # Clicks link containing the text
        self.assert_text('The blag', 'header h2')     # Asserts text in element
        self.update_text('input#s', 'Robots!\n')  # Updates textfield with text
        self.assert_text('Hooray robots!', '#content')
        self.open('http://xkcd.com/1319/')
        self.assert_text('Automation', 'div#ctitle')
```

Here's how to run the example script using various web browsers:

```bash
cd examples/

nosetests my_first_test.py --with-selenium --browser=chrome -s

nosetests my_first_test.py --with-selenium --browser=firefox -s

nosetests my_first_test.py --with-selenium --browser=phantomjs -s
```

After the test completes, in the console output you'll see a dot (``.``) on a new line, representing a passing test. (On test failures you'll see an ``F`` instead, and on test errors you'll see an ``E``). It looks more like a moving progress bar when you're running a ton of unit tests side by side. This is part of nosetests. After all tests complete (in this case there is only one), you'll see the "``Ran 1 test in ...``" line, followed by an "``OK``" if all nosetests passed. The ``--with-selenium`` option is required for running GUI tests. If no browser is specified, Chrome will become the default. The ``-s`` option is optional, and that makes sure that any standard output is printed immediately on the command line when tests have print statements in them, which makes debugging much easier.

NOTE: The following two lines of code can be simplified...
``` python
text = self.get_text(CSS_SELECTOR)
assert(TEXT_SEGMENT in text)
```
...into this one line:
``` python
self.assert_text(TEXT_SEGMENT, CSS_SELECTOR)
```

If the example test is moving too fast for your eyes to see what's going on, you can run it in Demo Mode by adding ``--demo_mode`` on the command line, which pauses the browser for about a second (by default) after each action, and highlights the element being acted on:

```bash
nosetests my_first_test.py --with-selenium --browser=chrome -s --demo_mode
```

You can override the default wait time by either updating [settings.py](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/config/settings.py) or by using ``--demo_sleep={NUM}`` when using Demo Mode. (NOTE: If you use ``--demo_sleep={NUM}`` without using ``--demo_mode``, nothing will happen.)

If you ever make any changes to your local copy of ``settings.py``, you may need to run ``python setup.py install`` for those changes to take effect.

```bash
nosetests my_first_test.py --with-selenium --browser=chrome -s --demo_mode --demo_sleep=1.2
```

You can also add either of the following to your scripts to slow down the tests:

```python
import time; time.sleep(5)  # sleep for 5 seconds (add this after the line you want to pause on)
import ipdb; ipdb.set_trace()  # waits for your command. n = next line of current method, c = continue, s = step / next executed line (will jump)
```

(NOTE: If you're using pytest instead of nosetests and you want to use ipdb in your script for debugging purposes, you'll either need to add "--capture=no" on the command line, or use "import pytest; pytest.set_trace()" instead of using ipdb. More info on that [here](http://stackoverflow.com/questions/2678792/can-i-debug-with-python-debugger-when-using-py-test-somehow).)

You may also want to have your test sleep in other situations where you need to have your test wait for something. If you know what you're waiting for, you should be specific by using a command that waits for something specific to happen.

If you need to debug things on the fly (in case of errors), use this line to run the code:

```bash
nosetests my_first_test.py --browser=chrome --with-selenium --pdb --pdb-failures -s
```

The above code (with --pdb) will leave your browser window open in case there's a failure, which is possible if the web pages from the example change the data that's displayed on the page. (ipdb commands: 'c', 's', 'n' => continue, step, next).

Here are some other useful nosetest arguments that you may want to append to your run commands:

```bash
--logging-level=INFO  # Hide DEBUG messages, which can be overwhelming.
-x  # Stop running the tests after the first failure is reached.
-v  # Prints the full test name rather than a dot for each test.
--with-id  # If -v is also used, will number the tests for easy counting.
```

Due to high demand, pytest support has been added. You can run the above sample script in pytest like this:

```bash
py.test my_first_test.py --with-selenium --with-testing_base --browser=firefox -s

py.test my_first_test.py --with-selenium --with-testing_base --browser=chrome -s

py.test my_first_test.py --with-selenium --with-testing_base --browser=phantomjs -s
```

(NOTE: If you're using pytest instead nosetests for running your own integration tests outside of the SeleniumBase file path, you'll need a copy of [conftest.py](https://github.com/seleniumbase/SeleniumBase/blob/master/conftest.py) inside your folder structure because the pytest configuration is defined there locally at runtime.)

(NOTE: The ``--with-testing_base`` plugin gives you full logging on test failures for screenshots, page source, and basic test info.)

**Creating Visual Test Suite Reports** (for nosetest users *ONLY*): The ``--report`` option gives you a fancy report after your test suite completes. (Requires ``--with-testing_base`` to also be set when ``--report`` is used)

```bash
nosetests my_test_suite.py --with-selenium --browser=chrome --with-testing_base --report -s
```
![](http://cdn2.hubspot.net/hubfs/100006/images/Test_Report_2.png "Example Test Report")

(NOTE: You can add ``--hide_report`` to immediately archive the report rather than displaying it after the test suite completes. You'll want to use this when running tests remotely because otherwise the test run will hang indefinitely until someone manually exits the report.)

#### **Step 5:** Complete the setup

If you're planning on using the full power of this test framework, there are a few more things you'll want to do:

* Setup your [Jenkins](http://jenkins-ci.org/) build server for running your tests at regular intervals. (Or you can use any build server you want.)

* Setup an [Amazon S3](http://aws.amazon.com/s3/) account for saving your log files and screenshots for future viewing. This test framework already has the code you need to connect to it. (Modify [settings.py](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/config/settings.py) with connection details to your instance.)

* Install [MySQL Workbench](http://dev.mysql.com/downloads/tools/workbench/) to make life easier by giving you a nice GUI tool that you can use to read & write from your DB directly.

* Setup your Selenium Grid and update your *.cfg file to point there. An example config file called selenium_server_config_example.cfg has been provided for you in the integrations/selenium_grid folder. The start-selenium-node.bat and start-selenium-server.sh files are for running your grid. In an example situation, your Selenium Grid server might live on a unix box and your Selenium Grid nodes might live on EC2 Windows virtual machines. When your build server runs a Selenium test, it would connect to your Selenium Grid to find out which Grid browser nodes are available to run that test. To simplify things, you can use [Browser Stack](https://www.browserstack.com/automate) as your entire Selenium Grid (and let them do all the fun work of maintaining the grid for you).

* There are ways of running your tests from Jenkins without having to utilize a remote machine. One way is by using PhantomJS as your browser (it runs headlessly). Another way is by using Xvfb (another headless system). [There's a plugin for Xvfb in Jenkins](https://wiki.jenkins-ci.org/display/JENKINS/Xvfb+Plugin).
If you have Xvfb running in the background, you can add ``--headless`` to your run command in order to utilize it. For information about the Xvfb plugin for Jenkins, [click here](http://qxf2.com/blog/xvfb-plugin-for-jenkins-selenium/).

* If you use [Slack](https://slack.com), you can easily have your Jenkins jobs display results there by using the [Jenkins Slack Plugin](https://github.com/jenkinsci/slack-plugin). Another way to send messages from your tests to Slack is by using [Slack's Incoming Webhooks API](https://api.slack.com/incoming-webhooks).

* If you use [HipChat](https://www.hipchat.com/), you can easily have your Jenkins jobs display results there by using the [Jenkins HipChat Plugin](https://wiki.jenkins-ci.org/display/JENKINS/HipChat+Plugin). Another way is by using the [hipchat_reporting plugin](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/plugins/hipchat_reporting_plugin.py) (nosetests only).

* Be sure to tell SeleniumBase to use these added features when you set them up. That's easy to do. You would be running tests like this:

```bash
nosetests [YOUR_TEST_FILE].py --browser=chrome --with-selenium --with-testing_base --with-db_reporting --with-s3_logging -s
```
(NOTE: Don't use ``--with-db_reporting`` or ``--with-s3_logging`` if you haven't configured your MySQL or S3 connections in [settings.py](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/config/settings.py))

When the testing_base plugin is used, if there's a test failure, the basic_test_info plugin records test logs, the page_source plugin records the page source of the last web page seen by the test, and the screen_shots plugin records the image of the last page seen by the test where the failure occurred. Make sure you always include testing_base whenever you include a plugin that logs test data. The db_reporting plugin records the status of all tests run into your MySQL DB. The s3_logging plugin uploads basic test info, screenshots, and page source into your S3 storage folder.

To simplify that long run command, you can create a *.cfg file, such as the one provided in the example, and enter your plugins there so that you can run everything by typing:

```bash
nosetests [YOUR_TEST_FILE].py --config=[MY_CONFIG_FILE].cfg -s
```

You can simplify that even more by using a setup.cfg file, such as the one provided for you in the examples folder. If you kick off a test run from within the folder that setup.cfg is location in, that file will automatically be used as your configuration, meaning that you wouldn't have to type out all the plugins that you want to use (or include a config file) everytime you run tests.

If you tell nosetests to run an entire file, it will run every method in that python file that starts with "test". You can be more specific on what to run by doing something like:

```bash
nosetests [YOUR_TEST_FILE].py:[SOME_CLASS_NAME].test_[SOME_TEST_NAME] --config=[MY_CONFIG_FILE].cfg -s
```

Let's try an example of a test that fails. Copy the following into a file called fail_test.py:
```python
""" test_fail.py """
from seleniumbase import BaseCase

class MyTestClass(BaseCase):

    def test_find_army_of_robots_on_xkcd_desert_island(self):
        self.open("http://xkcd.com/731/")
        self.assert_element("div#ARMY_OF_ROBOTS", timeout=3)  # This should fail
```
Now run it:

```bash
nosetests test_fail.py --browser=chrome --with-selenium --with-testing_base -s
```

You'll notice that a logs folder, "latest_logs", was created to hold information about the failing test, and screenshots. Take a look at what you get. Remember, this data can be saved in your MySQL DB and in S3 if you include the necessary plugins in your run command (and if you set up the neccessary connections properly). For future test runs, past test results will get stored in the archived_logs folder if you have ARCHIVE_EXISTING_LOGS set to True in [settings.py](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/config/settings.py).

Have you made it this far? Congratulations!!! Now you're ready to dive in at full speed!


### Part II: Detailed Method Specifications, Examples

#### Navigating to a Page, Plus Some Other Useful Related Commands

```python
self.open("https://xkcd.com/378/")  # Instant navigation to any web page.

self.driver.refresh()  # refresh/reload the current page.

where_am_i = self.driver.current_url  # this variable changes as the current page changes.

source = self.driver.page_source   # this variable changes as the page source changes.
```

**ProTip™:** You may need to use the page_source method along with Python's find() command to parse through the source to find something that Selenium wouldn't be able to. (You may want to brush up on your Python programming skills if you're confused.)
Ex:
```python
source = self.driver.page_source
first_image_open_tag = source.find('<img>')
first_image_close_tag = source.find'</img>', first_image_open_tag)
everything_inside_first_image_tags = source[first_image_open_tag+len('<img>'):first_image_close_tag]
```

#### Clicking

To click an element on the page:

```python
self.click("div#my_id")
```

#### Typing Text

self.update_text(selector, text)  # updates the text from the specified element with the specified value. An exception is raised if the element is missing or if the text field is not editable. Example:

```python
self.update_text("input#id_value", "2012")
```

You can also use self.add_text() or the WebDriver .send_keys() command, but those won't clear the text box first if there's already text inside.
If you want to type in special keys, that's easy too. Here's an example:

```python
from selenium.webdriver.common.keys import Keys
self.find_element("textarea").send_keys(Keys.SPACE + Keys.BACK_SPACE + '\n')  # the backspace should cancel out the space, leaving you with the newline
```

#### Getting the text from an element on a page

```python
self.get_text("header h2")
```

#### Asserting existance of an element on a page within some number of seconds:

```python
self.wait_for_element_present("div.my_class", timeout=10)
```
(NOTE: You can also use: ``self.assert_element_present(ELEMENT)``)

#### Asserting visibility of an element on a page within some number of seconds:

```python
self.wait_for_element_visible("a.my_class", timeout=5)
```
(NOTE: The short versions of this are ``self.find_element(ELEMENT)`` and ``self.assert_element(ELEMENT)``. The find_element() version returns the element)

Since the line above returns the element, you can combine that with .click() as shown below:

```python
self.find_element("a.my_class", timeout=5).click()

# But you're better off using the following statement, which does the same thing:

self.click("a.my_class")  # DO IT THIS WAY!
```

Using dots to signify class names is a simplified way of using ``*=`` within a CSS selector. That simplified version looks like this:

```python
self.click('a[class*="my_class"]')
```

**ProTip™:** You can use ``*=`` to search for any partial value in a CSS selector.

#### Asserting visibility of text inside an element on a page within some number of seconds:

```python
self.wait_for_text_visible("Make it so!", "div#trek div.picard div.quotes", timeout=3)
self.wait_for_text_visible("Tea. Earl Grey. Hot.", "div#trek div.picard div.quotes", timeout=1)
```
(NOTE: The short versions of this are ``self.find_text(TEXT, ELEMENT)`` and ``self.assert_text(TEXT, ELEMENT)``)

#### Asserting Anything

```python
self.assertTrue(myvar1 == something)

self.assertEqual(var1, var2)
```

#### Useful Conditional Statements (with creative examples in action)

is_element_visible(selector)  # is an element visible on a page
```python
import logging
if self.is_element_visible('div#warning'):
    logging.debug("Red Alert: Something bad might be happening!")
```

is_element_present(selector)  # is an element present on a page
```python
if self.is_element_present('div#top_secret img.tracking_cookie'):
    self.contact_cookie_monster()  # Not a real method unless you define it somewhere
else:
    current_url = self.driver.current_url
    self.contact_the_nsa(url=current_url, message="Dark Zone Found")  # Not a real method unless you define it somewhere
```
Another example:
```python
def is_there_a_cloaked_klingon_ship_on_this_page():
    if self.is_element_present("div.ships div.klingon"):
        return not self.is_element_visible("div.ships div.klingon")
    return False
```

is_text_visible(text, selector)  # is text visible on a page
```python
def get_mirror_universe_captain_picard_superbowl_ad(superbowl_year):
    selector = "div.superbowl_%s div.commercials div.transcript div.picard" % superbowl_year
    if self.is_text_visible("For the Love of Marketing and Earl Grey Tea!", selector):
        return "Picard HubSpot Superbowl Ad 2015"
    elif self.is_text_visible("Delivery Drones... Engage", selector):
        return "Picard Amazon Superbowl Ad 2015"
    elif self.is_text_visible("Bing it on Screen!", selector):
        return "Picard Microsoft Superbowl Ad 2015"
    elif self.is_text_visible("OK Glass, Make it So!", selector):
        return "Picard Google Superbowl Ad 2015"
    elif self.is_text_visible("Number One, I've Never Seen Anything Like It.", selector):
        return "Picard Tesla Superbowl Ad 2015"
    elif self.is_text_visible("""With the first link, the chain is forged.
                              The first speech censored, the first thought forbidden,
                              the first freedom denied, chains us all irrevocably.""", selector):
        return "Picard Wikimedia Superbowl Ad 2015"
    elif self.is_text_visible("Let us make sure history never forgets the name ... Facebook", selector):
        return "Picard Facebook Superbowl Ad 2015"
    else:
        raise Exception("Reports of my assimilation are greatly exaggerated.")
```

#### Switching Tabs

What if your test opens up a new tab/window and now you have more than one page? No problem. You need to specify which one you currently want Selenium to use. Switching between tabs/windows is easy:
Ex:

```python
self.driver.switch_to.window(self.driver.window_handles[1])  # this switches to the new tab
```

driver.window_handles is a list that will continually get updated when new windows/tabs appear (index numbering is auto-incrementing from 0, which represents the main window)

**ProTip™:** iFrames follow the same principle as new windows - you need to specify the iFrame if you want to take action on something in there
Ex:

```python
self.driver.switch_to.frame('ContentManagerTextBody_ifr')
# Now you can act inside the iFrame
# Do something cool (here)
self.driver.switch_to.default_content()  # exit the iFrame when you're done
```

#### Handle Pop-Up Alerts

What if your test makes an alert pop up in your browser? No problem. You need to switch to it and either accept it or dismiss it:
Ex:

```python
self.wait_for_and_accept_alert()

self.wait_for_and_dismiss_alert()
```

If you're not sure whether there's an alert before trying to accept or dismiss it, one way to handle that is to wrap your alert-handling code in a try/except block. Other methods such as .text and .send_keys() will also work with alerts.

#### Executing Custom jQuery Scripts:

jQuery is a powerful JavaScript library that allows you to perform advanced actions in a web browser.
If the web page you're on already has jQuery loaded, you can start executing jQuery scripts immediately.
You'd know this because the web page would contain something like the following in the HTML:

```html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"></script>
```

It's OK if you want to use jQuery on a page that doesn't have it loaded yet. To do so, run the following command first:

```python
self.activate_jquery()
```

Here are some examples of using jQuery in your scripts:
```python
self.execute_script('jQuery, window.scrollTo(0, 600)')  # Scrolling the page

self.execute_script("jQuery('#annoying-widget').hide()")  # Hiding elements on a page

self.execute_script("jQuery('#annoying-button a').remove()")  # Removing elements on a page

self.execute_script("jQuery('%s').mouseover()" % (mouse_over_item))  # Mouse-over elements on a page

self.execute_script("jQuery('input#the_id').val('my_text')")  # Fast text input on a page

self.execute_script("jQuery('div#dropdown a.link').click()")  # Click elements on a page

self.execute_script("return jQuery('div#amazing')[0].text")  # Returns the css "text" of the element given

self.execute_script("return jQuery('textarea')[2].value")  # Returns the css "value" of the 3rd textarea element on the page
```

In the following example, javascript is used to plant code on a page that Selenium can then touch after that:
```python
self.open(SOME_PAGE_TO_PLAY_WITH)
referral_link = '<a class="analytics test" href="%s">Free-Referral Button!</a>' % DESTINATION_URL
self.execute_script("document.body.innerHTML = \"%s\"" % referral_link)
self.click("a.analytics")  # Clicks the generated button
```

#### Using non-terminating verifications:

Let's say you want to verify multiple different elements on a web page in a single test, but you don't want the test to fail until you verified several elements at once so that you don't have to rerun the test to find more missing elements on the same page. That's where page checks come in. Here's the example:

```python
from seleniumbase import BaseCase

class MyTestClass(BaseCase):

    def test_non_terminating_checks(self):
        self.open('http://xkcd.com/993/')
        self.wait_for_element('#comic')
        self.check_assert_element('img[alt="Brand Identity"]')
        self.check_assert_element('img[alt="Rocket Ship"]')  # Will Fail
        self.check_assert_element('#comicmap')
        self.check_assert_text('Fake Item', '#middleContainer')  # Will Fail
        self.check_assert_text('Random', '#middleContainer')
        self.check_assert_element('a[name="Super Fake !!!"]')  # Will Fail
        self.process_checks()
```

``check_assert_element()`` and ``check_assert_text()`` will save any exceptions that would be raised.
To flush out all the failed checks into a single exception, make sure to call ``self.process_checks()`` at the end of your test method. If your test hits multiple pages, you can call ``self.process_checks()`` at the end of all your checks for a single page. This way, the screenshot from your log file will make the location where the checks were made.

### Part III: More Details

Nosetests automatically runs any python method that starts with "test" from the file you selected. You can also select specific tests to run from files or classes. For example, the code in the early examples could've been run using "nosetests my_first_test.py:MyTestClass.test_basic ... ...". If you wanted to run all tests in MyTestClass, you can use: "nosetests my_first_test.py:MyTestClass ... ...", which is useful when you have multiple tests in the same file. Don't forget the plugins. Use "-s" if you want better logging in the console output.

To use the SeleniumBase Test Framework calls, don't forget to include the following import:

```python
from seleniumbase import BaseCase
```

And you'll need to inherit BaseCase in your classes like so:

```python
class MyTestClass(BaseCase):
```

####  Checking Email: 
Let's say you have a test that sends an email, and now you want to check that the email was received:

```python
from seleniumbase.fixtures.email_manager import EmailManager, EmailException
num_email_results = 0
email_subject = "This is the subject to search for (maybe include a timestamp)"
email_manager = EmailManager("[YOUR SELENIUM GMAIL EMAIL ADDRESS]")  # the password for this is elsewhere (in the library) because this is a default email account
try:
    html_text = email_manager.search(SUBJECT="%s" % email_subject, timeout=300)
    num_email_results = len(html_text)
except EmailException:
    num_email_results = 0
self.assertTrue(num_email_results)  # true if not zero
```

Now you can parse through the email if you're looking for specific text or want to navigate to a link listed there.


####  Database Powers: 
Let's say you have a test that needs to access the database. First make sure you already have a table ready. Then try this example:

```python
from seleniumbase.core.mysql import DatabaseManager
def write_data_to_db(self, theId, theValue, theUrl):
    db = DatabaseManager()
    query = """INSERT INTO myTable(theId,theValue,theUrl)
               VALUES (%(theId)s,%(theValue)s,%(theUrl)s)"""
    db.execute_query_and_close(query, {"theId":theId,
                               "theValue":theValue,
                               "theUrl":theUrl})
```

Access credentials are stored in [settings.py](https://github.com/seleniumbase/SeleniumBase/blob/master/seleniumbase/config/settings.py) for your convenience (you have to add them first).

The following example below (taken from the Delayed Data Manager) shows how data can be pulled from the database.

```python
import logging
from seleniumbase.core.mysql import DatabaseManager

def get_delayed_test_data(self, testcase_address, done=0):
    """ Returns a list of rows """
    db = DatabaseManager()
    query = """SELECT guid,testcaseAddress,insertedAt,expectedResult,done
               FROM delayedTestData
               WHERE testcaseAddress=%(testcase_address)s
               AND done=%(done)s"""
    data = db.fetchall_query_and_close(query, {"testcase_address":testcase_address, "done":done})
    if data:
        return data
    else:
        logging.debug("Could not find any rows in delayedTestData.")
        logging.debug("DB Query = " + query % {"testcase_address":testcase_address, "done":done})
        return []
```

Now you know how to pull data from your MySQL DB.

You may also be wondering when you would use the Delayed Data Manager. Here's one example: If you scheduled an email to go out 12 hours from now and you wanted to check that the email gets received (but you don't want the Selenium test of a Jenkins job to sit idle for 12 hours) you can store the email credentials as a unique time-stamp for the email subject in the DB (along with a time for when it's safe for the email to be searched for) and then a later-running test can do the checking after the right amount of time has passed.


Congratulations! If you've made it this far, it means you have a pretty good idea about how to move forward!
Feel free to check out these other exciting open source projects on GitHub by some smart people I know:
[https://github.com/hubspot](https://github.com/hubspot)

Happy Automating!

~ Michael Mintz (https://github.com/mdmintz)


### Legal Disclaimer
Automation is a powerful thing. It allows you to take full control of web browsers and do almost anything that a human could do, but faster. It can be used for both good and evil. With great power comes great responsibility. You are fully responsible for how you use this platform and the automation that you create.
