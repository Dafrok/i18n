# Uso di Selenium e WebDriver

Da [ChromeDriver - WebDriver per Chrome][chrome-driver]:

> WebDriver è uno strumento open source per testare automaticamente le app web per vari browser. Fornisce funzioni per navigare alle pagine web, per l'input utente, per l'esecuzione degli JavaScript ed altro. ChromeDriver è un server autonomo che migliora il protocollo di WebDriver per Chromium. Esso è stato sviluppato dai membri dei team di Chromium e WebDriver.

## Impostare Spectron

[Spectron][spectron] è il ChromeDriver per testare i framework ufficialmente supportata per Electron. Essa è costruita sulla base di [WebdriverIO](http://webdriver.io/) ed ha degli aiuti per accedere alle API di Electron nei tuoi test e bundle di ChromeDriver.

```sh
$ npm install --save-dev spectron
```

```javascript
// A simple test to verify a visible window is opened with a title
const Application = require('spectron').Application
const assert = require('assert')

const myApp = new Application({
  path: '/Applications/MyApp.app/Contents/MacOS/MyApp'
})

const verifyWindowIsVisibleWithTitle = async (app) => {
  await app.start()
  try {
    // Check if the window is visible
    const isVisible = await app.browserWindow.isVisible()
    // Verify the window is visible
    assert.strictEqual(isVisible, true)
    // Get the window's title
    const title = await app.client.getTitle()
    // Verify the window's title
    assert.strictEqual(title, 'My App')
  } catch (error) {
    // Log any failures
    console.error('Test failed', error.message)
  }
  // Stop the application
  await app.stop()
}

verifyWindowIsVisibleWithTitle(myApp)
```

## Impostare WebDriverJs

[WebDriverJs](https://code.google.com/p/selenium/wiki/WebDriverJs) fornisce un pacchetto Node per testare con il driver web, lo useremo come esempio.

### 1. Avvia ChromeDriver

Prima devi scaricare il binario di `chromedriver` ed eseguirlo:

```sh
$ npm install electron-chromedriver
$ ./node_modules/.bin/chromedriver
Avviando ChromeDriver (v2.10.291558) sulla porta 9515
Solo connessioni locali consentite.
```

Ricorda il numero di porta `9515`, che sarà usato più tardi

### 2. Install WebDriverJS

```sh
$ npm install selenium-webdriver
```

### 3. Connettiti a ChromeDriver

L'utilizzo di `selenio-webdriver` con Electron è lo stesso con a monte, tranne che è necessario specificare manualmente come collegare driver cromo e dove trovare il binario di Electron:

```javascript
const webdriver = require('selenium-webdriver')

const driver = new webdriver.Builder()
  // La "9515" è la porta aperta da chrome driver.
  .usareServer('http://localhost:9515')
  .conFunzioni({
    chromeOpzioni: {
      // Qui è il precorso al tuo binario di Electron.
      binary: '/Path-to-Your-App.app/Contents/MacOS/Electron'
    }
  })
  .forBrowser('electron')
  .build()

driver.get('http://www.google.com')
driver.findElement(webdriver.By.name('q')).sendKeys('webdriver')
driver.findElement(webdriver.By.name('btnG')).click()
driver.wait(() => {
  return driver.getTitle().then((title) => {
    return title === 'webdriver - Google Search'
  })
}, 1000)

driver.quit()
```

## Impostare WebdriverIO

[WebdriverIO](http://webdriver.io/) fornisce un pacchetto Node per testare con il driver web.

### 1. Avvia ChromeDriver

Prima devi scaricare il binario di `chromedriver` ed eseguirlo:

```sh
$ npm install electron-chromedriver
$ ./node_modules/.bin/chromedriver --url-base=wd/hub --port=9515
Avviando ChromeDriver (v2.10.291558) sulla porta 9515
Solo connessioni locali consentite.
```

Ricorda il numero di porta `9515`, che sarà usato più tardi

### 2. Installa WebdriverIO

```sh
$ npm install webdriverio
```

### 3. Connettiti al driver cromato

```javascript
const webdriverio = require('webdriverio')
const options = {
  host: 'localhost', // Use localhost as chrome driver server
  port: 9515, // "9515" is the port opened by chrome driver.
  desiredCapabilities: {
    browserName: 'chrome',
    'goog:chromeOptions': {
      binary: '/Path-to-Your-App/electron', // Path to your Electron binary.
      args: [/* cli arguments */] // Optional, perhaps 'app=' + /path/to/your/app/
    }
  }
}

let client = webdriverio.remote(options)

client
  .init()
  .url('http://google.com')
  .setValue('#q', 'webdriverio')
  .click('#btnG')
  .getTitle().then((title) => {
    console.log('Title was: ' + title)
  })
  .end()
```

## Workflow

Per testare la tua applicazione senza ricostruire Electron, [posiziona](https://github.com/electron/electron/blob/master/docs/tutorial/application-distribution.md) la sorgente della tua app nella directory delle risorse di Electron.

In alternativa, passa un argomento da eseguire con il binario Electron che punta alla cartella della tua app. Questo elimina la necessità di copiare-incollare la tua app nella directory delle risorse di Electron.

[chrome-driver]: https://sites.google.com/a/chromium.org/chromedriver/
[spectron]: https://electronjs.org/spectron
