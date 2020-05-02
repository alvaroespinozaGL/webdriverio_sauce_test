# webdriverio_sauce_test
Node.js with webdriverio automated testing project from scratch and follow the structure learned in the video to create tests against the following website:  https://www.saucedemo.com/

The structure contains tests, functions and elements for the following pages: login, inventory, items (products), cart, checkout.

## before running the test:

These requirements need to be met (download and install from the official pages):

1-Installing NodeJS and NPM(https://nodejs.org/en/)

2-Installing Visual Studio Code(https://code.visualstudio.com/)


## Installing the project and dependencies.
Follow these steps:

1- Clone the repository
    
```bash
git clone https://github.com/alvaroespinozaGL/webdriverio_sauce_test.git
cd webdriverio_sauce_test # to move into the repository folder.
```

2- Install webdriverIO. 
```bash
npm init  # to create package.json file.
npm install webdriverio --save-dev #all webdriverio dependencies will be added to package.json
```
3- create Wdio config file
```bash
npm install @wdio/cli #installing wdio cli package
./node_modules/.bin/wdio config #installing wdio config dependencies
```
./node_modules/.bin/wdio config
=========================
WDIO Configuration Helper
=========================

? Where should your tests be launched? local
? Where is your automation backend located? On my local machine
? Which framework do you want to use? mocha 
? Do you want to run WebdriverIO commands synchronous or asynchronous? sync
? Where are your test specs located? ./test/specs/**/*.js
? Which reporter do you want to use? spec
? Do you want to add a service to your test setup? selenium-standalone
? What is the base url? https://www.saucedemo.com/

4- Install Chai
Chai is going to be the assertion library that we're going to use. So, we're going to say:
```bash
npm install chai --save-dev
```
We are also going to install Chai WebdriverIO so that further on we can use it to set global assertions.
```bash
npm install chai-webdriverio --save-dev
```
## NOTE
When we say --save it allows it to be saved to our package.json so that whenever we say npm install, if it is that we lose our node_modules, or if it is that we are uploading it to our repository, other persons when they're using the project can just say npm install and all of the packages that we use, which will be stored in our package.json, will be unloaded for them and they will have their own node_modules folder.

5- install our local runner.
```bash
npm install local-runner --save-dev
```

6- Let us now set this up in our configuration file so that we can use Chai assertion throughout our project.

We are going to go into our configuration file [wdio.conf.js] and we are going to go to the beforeTest section. Let's uncomment it.

What we are doing is adding the Chai assertions.

We can use assert, we can use expect, we can use should, as the Chai module contains all those three assertions. We're putting it in the “before” snippet because it will run the containing code before every test, regardless of where the file is stored.

In this case, we're going to be setting global asserts, global should, and global expect, so that we won't need to import it in every file.

Now, we are going to say:
```bash
   beforeTest: function () {
        const chai = require('chai')
        const chaiWebdriver = require('chai-webdriverio').default
        chai.use(chaiWebdriver(browser))
        global.assert = chai.assert
        global.should = chai.should
        global.expect = chai.expect
    },
```


## Files structure.  
- `node_module` folder: all the dependency packages are stored.
- `package.json` file: This file contains the dependencies for our project.

## Run the test cases.
Follow these steps/examples.

1- Run all test cases with default configurations:
```bash
npm test
```
2- Run all tests in Firefox
```bash
npm run test-firefox  # this is an alias that will run "cypress run -b firefox"
```
3- Run all tests in Chrome
```bash
npm run test-chrome  # this is an alias that will run "cypress run -b chrome"
```

Of course the tests can also be executed without this script configurations as the follow examples, we can use and combine whatever we need based on the cypress flags:
```bash 
./node_modules/.bin/cypress run 
./node_modules/.bin/cypress run -b chrome # run test cases in chrome not headless
./node_modules/.bin/cypress run -b firefox # run test cases in firefox not headless
./node_modules/.bin/cypress run -b chrome --headless # run test cases in chrome headless
```
