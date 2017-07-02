# Why the test automation

Vastly Increases Your Test Coverage. Automated software testing can increase the depth and scope of tests to help improve software quality. Lengthy tests that are often avoided during manual testing can be run unattended. They can even be run on multiple computers with different configurations.

# Selenium Automation Testing

Selenium is a browser automation library, most often used for testing web applications. Selenium may be used for any task that requires automating interaction with the browser. 

# Support Programming Languages

Java / Python / Ruby / C# / Go / JavaScript

# How to start

Node.js required: https://nodejs.org/en/

Selenium may be installed via npm 

$ npm install selenium-webdriver

(Note: Mozilla's geckodriver is only required for Firefox 47+. Everything you need for Firefox 38 - 46 is included with this package. )

Browsers and Drivers: 

Chrome -> chromedriver.exe

Internet Explorer -> IEDriverServer.exe

Edge -> MicrosoftWebDriver.msi

Firefox 47+ -> geckodriver.exe

PhantomJS -> phantomjs.exe

Opera -> operadriver.exe

Safari -> SafariDriver.safariextz

You will need to download additional components to work with each of the major browsers. The drivers for Chrome, Firefox, PhantomJS, Opera, IE and Edge web browsers are all standalone executables that should be placed on your system PATH. The SafariDriverBrowser extension should be installed in your browser before using Selenium. Recommend that disabling the extension when using the browser without Selenium or installing the extension in a profile only used for testing. 

$ cd node-app

$ cat > test.js

# Sample Code

var webdriver = require('selenium-webdriver')

var by = webdriver.By

var until = webdriver.until

var driver = new webdriver

   .Builder()
   
   .withCapabilities(webdriver.Capabilities.chrome())
   
   .build()
   
// var driver = new webdriver

//   .Builder()

//   .forBrowser('firefox')

//   .build()
 
driver.get('http://www.google.com')

driver.findElement(webdriver.By.name('q')).sendKeys('simple programmer')

driver.findElement(webdriver.By.name('btnG')).click()

driver.wait(until.titleIs('webdriver-google-search'))

driver.quit()

# Run

$ node test.js

# References

https://seleniumhq.github.io/selenium/docs/api/javascript/index.html
https://www.ibm.com/developerworks/library/a-automating-ria/index.html







