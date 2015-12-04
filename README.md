# SeleniumBase Automation Framework

### An open-source solution for reliable testing and business automation.

Trusted by Boston's most promising companies, including HubSpot, Jana, and Veracode.

#### Features include:
* Python libraries for quickly making reliable WebDriver scripts that run fast.
* Built-in Nosetest & Pytest plugins for logging test data, results, and screenshots.
* Simple integration with [Jenkins](http://jenkins-ci.org/), [Selenium Grid](http://docs.seleniumhq.org/projects/grid/), [MySQL](http://www.mysql.com/), [Docker](https://www.docker.com/), and [AWS](http://aws.amazon.com/).
* Customizable with command-line options and a global config file: [settings.py](https://github.com/mdmintz/SeleniumBase/blob/master/seleniumbase/config/settings.py).

*Learn how the pros handle test automation: Check out HubSpot's blog article on [Automated Testing with Selenium](http://dev.hubspot.com/blog/bid/88880/Automated-Integration-Testing-with-Selenium-at-HubSpot), and read [The Classic "QA Team" is Obsolete](http://product.hubspot.com/blog/the-classic-qa-team-is-obsolete) for more.*


## Part I: MAC SETUP INSTRUCTIONS
####(WINDOWS users: You'll need to make a few modifications to the setup steps listed here. For starters, you won't be able to use the "brew install" command since that's MAC-only. Instead, download the requirements mentioned directly from the web. I'll provide you with links to save you time. You'll also want to put downloaded files into your [PATH](http://java.com/en/download/help/path.xml).)
####(DOCKER users: If you want to run browser automation with Docker, see the [Docker_README](https://github.com/mdmintz/SeleniumBase/blob/master/Docker_README.md))

#### **Step 0:** Get the requirements

[Python 2.*](https://www.python.org/downloads/)

If you're a MAC user, that should already come preinstalled on your machine. Although Python 3 exists, you'll want Python 2 (both of these major versions are being improved in parallel). Python 2.7.10 is the one I've been using on my Mac.

If you're a WINDOWS user, [download the latest 2.* version from here](https://www.python.org/downloads/release/python-2710/). Depending on which version of Python you have installed, you may need to install "pip" if your Python installation didn't come with it. If you don't have it installed, you can [get pip here](https://pip.pypa.io/en/latest/installing/).

[Homebrew](http://brew.sh/) + [Git](http://git-scm.com/)

(NOTE: You can download the SeleniumBase repository right from GitHub and skip all the git-related commands. That's probably the fastest way if you want to quickly get a live demo of this tool up and running.)

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    brew install git
    brew update

(WINDOWS users: Skip the Homebrew part and [download Git here](http://git-scm.com/download).)

[MySQL](http://www.mysql.com/)

(NOTE: If you're using this test framework from a local development machine and don't plan on writing to a MySQL DB from your local test runs, you can skip this step.)

    brew install MySQL

That installs the MySQL library so that you can use db commands in your code. To make that useful, you'll want to have a MySQL DB that you can connect to. You'll also want to use the testcaserepository.sql file from the seleniumbase/core folder to add the necessary tables.

(WINDOWS users: [Download MySQL here](http://dev.mysql.com/downloads/windows/). If you want a visual tool to help make your MySQL life easier, [try MySQL Workbench](http://dev.mysql.com/downloads/workbench/).)

[virtualenvwrapper](http://virtualenvwrapper.readthedocs.org/en/latest/)

    cd ~/
    pip install virtualenvwrapper
    export WORKON_HOME=~/Envs
    mkdir -p $WORKON_HOME
    source /usr/local/bin/virtualenvwrapper.sh

To save time from having to source virtualenvwrapper again when you open a new window, you can add the line "source /usr/local/bin/virtualenvwrapper.sh" to a file called ".bash_profile" in your home directory.

    cd ~/
    vi .bash_profile
    source /usr/local/bin/virtualenvwrapper.sh

("vi" is a fast text editor - "i" for insert-text mode, "esc" to get out of insert-text mode, ":wq"+[Enter] to save & exit the file)

[Chromedriver](https://sites.google.com/a/chromium.org/chromedriver/) and [PhantomJS](http://phantomjs.org/)

    brew install chromedriver phantomjs

(NOTE: There are web drivers for other web browsers as well. These two will get you started.)

(WINDOWS users: [Download Chromedriver](https://sites.google.com/a/chromium.org/chromedriver/downloads) and put it in your PATH. Next, [Download PhantomJS](https://bitbucket.org/ariya/phantomjs/downloads) and also put that in your PATH.)

If you haven't already, you'll want to [Download Firefox](https://www.mozilla.org/en-US/firefox/new/) and either [Download Chrome](https://www.google.com/chrome/browser/desktop/index.html) or [Download Chromium](https://download-chromium.appspot.com/).


#### **Step 1:** Download or Clone SeleniumBase to your local machine

If you're using Git, you can fork the repository on GitHub to create your personal copy. This is important because you'll want to add your own configurations, credentials, settings, etc. Now you can clone your forked copy to your personal computer. You can use a tool such as [SourceTree](http://www.sourcetreeapp.com/) to make things easier by providing you with a simple-to-use user interface for viewing and managing your git commits and status.

```bash
git clone [LOCATION OF YOUR FORKED SELENIUMBASE GITHUB FOLDER]/seleniumbase.git
cd seleniumbase
```

(NOTE: If you decided to download SeleniumBase rather than Git-cloning it, you can skip the above step.)

#### **Step 2:** Create a virtualenv for seleniumbase

```bash
mkvirtualenv seleniumbase
```

(Virtual environments are important because they allow you to have separate configurations from the rest of your system. This will prevent conflicts if you use other tools that require other configurations and settings.)

If you ever need to leave your virtual environment, use the following command:

```bash
deactivate
```

To get back into your virtual environment, use the following command:

```bash
workon seleniumbase
```

To see a list of environments that exist on your system, use the following command:

```bash
lsvirtualenv
```

To delete a virtual environment that you no longer need, use the following command:

```bash
rmvirtualenv [NAME OF VIRTUAL ENV TO REMOVE]
```

#### **Step 3:** Install necessary packages from the SeleniumBase folder and compile the test framework

If you don't desire connecting to a MySQL DB to record the results of your local test runs, run this command:

```bash
sudo pip install -r requirements.txt
```
The "-e ." at the end of requirements.txt should automatically trigger setup.py installation from the following command:
```bash
sudo python setup.py install
```

If you do desire connecting to a MySQL DB to record the results of your test runs, run this command: (Make sure you already have MySQL installed from either Brew or web-download. If you're a WINDOWS user, you may have problems on the MySQL installation part. To get around this, you can either follow the instructions from the error message given, or you can pip install the previous requirements.txt file.)

```bash
sudo pip install -r server_requirements.txt
```

As mentioned before, the "-e ." in that file should automatically trigger installation of setup.py

NOTE:

(If you already have root access on the machine you're using, you might not need to add "sudo" before those commands.)

In some cames, certain packages will have other dependencies as requirements, and those will get installed automatically. You'll be able to see all installed packages in your virtual environment by using the following command:

```bash
pip freeze
```

By default, some files may be hidden on a MAC, such as .gitignore (which is used to tell Git which files to ignore for staging commits). To view all files from the Finder window, run the following command in a terminal window:

```bash
defaults write com.apple.finder AppleShowAllFiles -bool true
```

(You may need to reopen the MAC Finder window to see changes from that.)


#### **Step 4:** Verify that Selenium and Chromedriver were successfully installed by checking inside a python command prompt

```bash
python
>>> from selenium import webdriver
>>> browser = webdriver.Chrome()
>>> browser.get("http://dev.hubspot.com/blog/the-classic-qa-team-is-obsolete")
>>> browser.close()
>>> exit()
```


#### **Step 5:** Verify that SeleniumBase was successfully installed by running example tests

You can verify the installation of SeleniumBase by writing a simple script to perform basic actions such as navigating to a web page, clicking, waiting for page elements to appear, typing in text, scraping text on a page, and verifying text. (Copy/paste the following code into a new file called "my_first_test.py"). This may be a good time to read up on css selectors. If you use Chrome, you can right-click on a page and select "Inspect Element" to see the details you need to create such a script. At a quick glance, dots are for class names and pound signs are for IDs.

```python
from seleniumbase import BaseCase

class MyTestClass(BaseCase):

    def test_basic(self):
        self.open("http://xkcd.com/353/")
        self.wait_for_element_visible("div#comic")
        self.click('a[rel="license"]')
        text = self.wait_for_element_visible('center').text
        self.assertTrue("reuse any of my drawings" in text)
        self.assertTrue("You can use them freely" in text)
        self.open("http://xkcd.com/1481/")
        self.click_link_text('Blag')
        self.wait_for_text_visible("The blag of the webcomic", "#site-description")
        self.update_text_value("input#s", "Robots!\n")
        self.wait_for_text_visible("Hooray robots!", "#content")
        self.open("http://xkcd.com/1319/")
        self.wait_for_text_visible("Automation", "div#ctitle")
```

Now try running the script using various web browsers:

```bash
nosetests my_first_test.py --browser=chrome --with-selenium -s

nosetests my_first_test.py --browser=phantomjs --with-selenium -s

nosetests my_first_test.py --browser=firefox --with-selenium -s
```

After the test completes, in the console output you'll see a dot on a new line, representing a passing test. (On test failures you'll see an F instead, and on test errors you'll see an E). It looks more like a moving progress bar when you're running a ton of unit tests side by side. This is part of nosetests. After all tests complete (in this case there is only one), you'll see the "Ran 1 test in ..." line, followed by an "OK" if all nosetests passed.
If the example is moving too fast for your eyes to see what's going on, there are 2 things you can do. Add either of the following:

```python
import time; time.sleep(5) # sleep for 5 seconds (add this after the line you want to pause on)
import ipdb; ipdb.set_trace() # waits for your command. n = next line of current method, c = continue, s = step / next executed line (will jump)
```

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
py.test my_first_test.py --with-selenium --with-testing_base --browser=chrome -s

py.test my_first_test.py --with-selenium --with-testing_base --browser=phantomjs -s

py.test my_first_test.py --with-selenium --with-testing_base --browser=firefox -s
```

(NOTE: I'm currently adding more pytest plugins to catch up with nosetests. The latest one added is "--with-testing_base", which gives you full logging on test failures for screenshots, page source, and basic test info. Coming soon: The DB and S3 plugins, which are already available with nosetests.)

#### **Step 6:** Complete the setup

If you're planning on using the full power of this test framework, there are a few more things you'll want to do:

* Setup your [Jenkins](http://jenkins-ci.org/) build server for running your tests at regular intervals. (Or you can use any build server you want.)

* Setup an [Amazon S3](http://aws.amazon.com/s3/) account for saving your log files and screenshots for future viewing. This test framework already has the code you need to connect to it. (Modify the s3_manager.py file from the seleniumbase/core folder with connection details to your instance.)

* Install [MySQL Workbench](http://dev.mysql.com/downloads/tools/workbench/) to make life easier by giving you a nice GUI tool that you can use to read & write from your DB directly.

* Setup your Selenium Grid and update your *.cfg file to point there. An example config file called selenium_server_config_example.cfg has been provided for you in the grid folder. The start-selenium-node.bat and start-selenium-server.sh files are for running your grid. In an example situation, your Selenium Grid server might live on a unix box and your Selenium Grid nodes might live on EC2 Windows virtual machines. When your build server runs a Selenium test, it would connect to your Selenium Grid to find out which Grid browser nodes are available to run that test. To simplify things, you can use [Browser Stack](https://www.browserstack.com/automate) as your entire Selenium Grid (and let them do all the fun work of maintaining the grid for you).

* There are ways of running your tests from Jenkins without having to utilize a remote machine. One way is by using PhantomJS as your browser (it runs headlessly). Another way is by using Xvfb (another headless system). [There's a plugin for Xvfb in Jenkins](https://wiki.jenkins-ci.org/display/JENKINS/Xvfb+Plugin). Here are some more helpful resources I found regarding the use of Xvfb:
1. http://stackoverflow.com/questions/6183276/how-do-i-run-selenium-in-xvfb
2. http://qxf2.com/blog/xvfb-plugin-for-jenkins-selenium/
3. http://stackoverflow.com/questions/27202131/firefox-started-by-selenium-ignores-the-display-created-by-pyvirtualdisplay

* If you use [Slack](https://slack.com), you can easily have your Jenkins jobs display results there by using the [Jenkins Slack Plugin](https://github.com/jenkinsci/slack-plugin). Another way to send messages from your tests to Slack is by using [Slack's Incoming Webhooks API](https://api.slack.com/incoming-webhooks).

* If you use [HipChat](https://www.hipchat.com/), you can easily have your Jenkins jobs display results there by using the [Jenkins HipChat Plugin](https://wiki.jenkins-ci.org/display/JENKINS/HipChat+Plugin). Another way is by using the hipchat_reporting plugin, which is included with this test framework.

* Be sure to tell SeleniumBase to use these added features when you set them up. That's easy to do. You would be running tests like this:

```bash
nosetests [YOUR_TEST_FILE].py --browser=chrome --with-selenium --with-testing_base --with-basic_test_info --with-page_source --with-screen_shots --with-db_reporting --with-s3_logging -s
```

(When the testing_base plugin is used, if there's a test failure, the basic_test_info plugin records test logs, the page_source plugin records the page source of the last web page seen by the test, and the screen_shots plugin records the image of the last page seen by the test where the failure occurred. Make sure you always include testing_base whenever you include a plugin that logs test data. The db_reporting plugin records the status of all tests as long as you've setup your MySQL DB properly and you've also updated your seleniumbase/core/mysql_conf.py file with your DB credentials.)
To simplify that long run command, you can create a *.cfg file, such as the one provided in the example, and enter your plugins there so that you can run everything by typing:

```bash
nosetests [YOUR_TEST_FILE].py --config=[MY_CONFIG_FILE].cfg -s
```

So much easier on the eyes :)
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
        self.driver.get("http://xkcd.com/731/")
        self.wait_for_element_visible("div#ARMY_OF_ROBOTS", timeout=3)  # This should fail
```
Now run it:

```bash
nosetests test_fail.py --browser=chrome --with-selenium --with-testing_base --with-basic_test_info --with-page_source --with-screen_shots -s
```

You'll notice that a logs folder was created to hold information about the failing test, and screenshots. Take a look at what you get. Remember, this data can be saved in your MySQL DB and in S3 if you include the necessary plugins in your run command (and if you set up the neccessary connections properly). For future test runs, past test results will get stored in the archived_logs folder.

Have you made it this far? Congratulations!!! Now you're ready to dive in at full speed!


## Part II: Detailed Method Specifications, Examples

#### Navigating to a Page, Plus Some Other Useful Related Commands

```python
self.driver.get("https://xkcd.com/378/")  # Instant navigation to any web page.

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

#### Asserting existance of an element on a page within some number of seconds:

```python
self.wait_for_element_present("div.my_class", timeout=10)
```

#### Asserting visibility of an element on a page within some number of seconds:

```python
self.wait_for_element_visible("a.my_class", timeout=5)
```

You can even combine visibility checking and clicking into one statement like so:

```python
self.wait_for_element_visible("a.my_class", timeout=5).click()
```

#### Asserting visibility of text inside an element on a page within some number of seconds:

```python
self.wait_for_text_visible("Make it so!", "div#trek div.picard div.quotes", timeout=3)
self.wait_for_text_visible("Tea. Earl Grey. Hot.", "div#trek div.picard div.quotes", timeout=1)
```

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

#### Typing Text

update_text_value(selector, text)  # updates the text from the specified element with the specified value. Exception raised if element missing or field not editable. Example:

```python
self.update_text_value("input#id_value", "2012")
```

You can also use the WebDriver .send_keys() command, but it won't clear the text box first if there's already text inside.
If you want to type in special keys, that's easy too. Here's an example:

```python
from selenium.webdriver.common.keys import Keys
self.wait_for_element_visible("textarea").send_keys(Keys.SPACE + Keys.BACK_SPACE + '\n')  # the backspace should cancel out the space, leaving you with the newline
```

#### Switching Tabs

What if your test opens up a new tab/window and now you have more than one page? No problem. You need to specify which one you currently want Selenium to use. Switching between tabs/windows is easy:
Ex:

```python
self.driver.switch_to_window(self.driver.window_handles[1])  # this switches to the new tab
```

driver.window_handles is a list that will continually get updated when new windows/tabs appear (index numbering is auto-incrementing from 0, which represents the main window)

**ProTip™:** iFrames follow the same principle as new windows - you need to specify the iFrame if you want to take action on something in there
Ex:

```python
self.driver.switch_to_frame('ContentManagerTextBody_ifr')
# Now you can act inside the iFrame
# Do something cool (here)
self.driver.switch_to_default_content()  # exit the iFrame when you're done
```

#### Handle Pop-Up Alerts

What if your test makes an alert pop up in your browser? No problem. You need to switch to it and either accept it or dismiss it:
Ex:

```python
self.driver.switch_to_alert().accept()

self.driver.switch_to_alert().dismiss()
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

In the following more-complex example, jQuery is used to plant code on a page that Selenium can then touch after that:
```python
self.driver.get(SOME_PAGE_TO_PLAY_WITH)
referral_link = '<a class="analytics test" href="%s">Free-Referral Button!</a>' % DESTINATION_URL
self.execute_script("document.body.innerHTML = \"%s\"" % referral_link)
self.click("a.analytics")  # Clicks the generated button
```

## Part III: More Details

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

Access credentials are stored in your library file for your convenience (you have to add them first).

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
Feel free to check out other exciting open source projects on GitHub:
[https://github.com/hubspot](https://github.com/hubspot)

Happy Automating!

~ Michael Mintz (https://github.com/mdmintz)


### Legal Disclaimer
Automation is a powerful tool. It allows you to take full control of web browsers and do almost anything that a human could do, but faster. It can be used for both good and evil. With great power comes great responsibility. You are fully responsible for how you use this framework and the automation that you create. You may also want to see an expert when it comes to setting up your automation environment if you require assistance.
