# Quick Start

If you are new to UI automation test or cross-platform automation tool, the basic idea is

0. You have a test target, such as a website, or an mobile app.
0. You need to write some test codes to validate the properties and state of UI elements of your target.
0. Your test codes talk to Macaca, and Macaca talks to your target, execute what you have commanded in your test codes such as switching between screens, inputting text you predefined, return the UI element and properties you described in your test code, and generate a report about pass or failure. 
Watching the following videos will help you understand the concepts better.

If you have done some UI automation before, you probably have grasped what Macaca can do. You might want to jum right into what's capability. 
We prepare an example for you to get a taste.

## Examples

Check out the sample located in this repo([sample-nodejs](//github.com/macaca-sample/sample-nodejs)).

```bash
$ git clone https://github.com/macaca-sample/sample-nodejs.git --depth=1
$ cd sample-nodejs
$ npm i
$ npm run doctor
$ npm run test:ios
```

### Run test tasks

```bash
# run test in current cwd
$ macaca run --verbose

# run test in a pointed directry and set a framework
# mocha, jasmine, tman, ava supported for Node.js env.
$ macaca run -d ./test -f mocha

# output log file as html code
$ macaca run -o

# run in silence, desktop only
$ macaca run --no-window

# custom mocha reporter
$ CUSTOM_DIR=path/to/screenshot macaca run -d ./test --reporter macaca-simple-reportor
```

Check out the sample located in this repo([macaca-electron-app-sample](//github.com/macaca-sample/macaca-electron-app-sample)).

```bash
# Install dependencies
$ npm i
$ npm run build
$ npm run dist
```
### Run test tasks
```bash
# Mac
$ npm run mac-start
$ npm run test

# Windows
$ npm run win-start
$ npm run win-server
$ npm run test
```
## Usage
```javascript

// Import official webdriver client package

const wd = require('macaca-wd');

describe('test electron.app', function() {
  this.timeout(5 * 60 * 1000);                     // Set timeout
  const driver = wd.promiseChainRemote({           // After this, the driver can directly use method chaining
    host: 'localhost',                             // Configure the host and port of the Macaca server that the webdriver client will connec to
    port: process.env.MACACA_SERVER_PORT || 3456   // MMacaca server defaults to using port 3456
  });

  before(function () {
    return driver.init({
      platformName: 'desktop',    //Set support Desktop parameters
      browserName: 'chrome',      //Set support Eletron parameters
      chromeOptions: {            //Set chromeDriver chromeOptions object parameters
        "binary": "/Applications/macaca-electron-builder.app/Contents/MacOS/macaca-electron-builder" // Electron path
      }
    }).sleep(2 * 1000)
  });

  after(function () {
    return driver
      .sleep(1000)
      .close()
  })

  it('click link', function () {
    return driver
      .waitForElementById('macacaId', 5000, 100)
      .click()
  })

  it('click button', function () {
    return driver
      .elementByCss('#app > div > header > div.sidebar-button')
      .click()
  })
  ...
})
```

### Start webdriver server only

```bash
# normal usage
$ macaca server --verbose

# set a port
$ macaca server -p 3456
```

### Environment doctor

```bash
$ macaca doctor
```

### More Help

```bash
$ macaca -h

# helper for server
$ macaca server -h

# helper for how to run test
$ macaca run -h
```

## Sample Video

### iOS APP

<video src="//os.alipayobjects.com/rmsportal/fyuMolxdSsGMlNw.mp4" controls="controls" preload="auto" controlslist="nodownload"></video>

### Mobile Safari

<video src="//os.alipayobjects.com/rmsportal/TDeTXmTfeqRlxhj.mp4" controls="controls" preload="auto" controlslist="nodownload"></video>

### Android APP

<video src="//os.alipayobjects.com/rmsportal/vjoZfJaZmCvInDv.mp4" controls="controls" preload="auto" controlslist="nodownload"></video>

### Android Browser

<video src="//os.alipayobjects.com/rmsportal/VoxFKOVDsOjKyMs.mp4" controls="controls" preload="auto" controlslist="nodownload"></video>

### Desktop (Electron)

<video src="//os.alipayobjects.com/rmsportal/bgBKHXYSrlYpuvv.mp4" controls="controls" preload="auto" controlslist="nodownload"></video>

## More Examples

[more sample](//github.com/macaca-sample).
