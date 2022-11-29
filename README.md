<h1 align="center">Uploader Form</h1>

<div align="center">
  <h3>
  <a href="https://docs.openaerialmap.org/ecosystem/getting-started/">Ecosystem</a>
  <span> | </span>
  <a href="https://github.com/hotosm/oam-uploader-api">Uploader API</a>
  <span> | </span>
  <a href="https://github.com/hotosm/oam-uploader-admin">Token Manager</a>
  </h3>
</div>

The Uploader Interface allows users to upload imagery that will be processed and stored in an [OpenImageryNetwork](https://github.com/openimagerynetwork/oin-metadata-spec) compatible bucket through a form. This web application requires the [Uploader API](https://github.com/hotosm/oam-uploader-api) to be running, and requires a token issued by the [Token Manager](https://github.com/hotosm/oam-uploader-admin). Before proceeding, we suggest you read the ecosystem docs.(上傳器界面允許用戶上傳圖像，這些圖像將通過表單處理並存儲在OpenImageryNetwork兼容存儲桶中。此 Web 應用程序需要運行Uploader API，並且需要Token Manager 的 token issued 。在繼續之前，我們建議您閱讀ecosystem docs。)

## Installation and Usage(安裝與使用)

The steps below will walk you through setting up your own instance of the oam-uploader.
(下面的步驟將引導您設置您自己的 oam-uploader 實例。)

### Install Project Dependencies(安裝依賴的項目)
To set up the development environment for this website, you'll need to install the following on your system:
(要為本網站設置開發環境，您需要在您的系統上安裝以下內容)

- [Node](http://nodejs.org/) v4 (To manage multiple node versions we recommend [nvm](https://github.com/creationix/nvm))

### Install Application Dependencies(安裝依賴的應用)

If you use [`nvm`](https://github.com/creationix/nvm), activate the desired Node version:
(如果你使用[`nvm`](https://github.com/creationix/nvm),啟用需要的Node版本)

```
nvm install
```

Install Node modules:
(安裝Node模板)

```
npm install
```

### Usage
(用法)

#### Config files
All the config files can be found in `app/assets/scripts/config`.
After installing the projects there will be 3 main files:
(所有的配置文件都可以在`app/assets/scripts/config`找到. 安裝項目後，將有 3 個主要文件：)
  - `local.js` - Used only for local development. On production this file should not exist or be empty.
                 (僅用於本地開發。在環境中，該文件不應存在或為空。)
  - `staging.js`
  - `production.js`

The `production.js` file serves as base and the other 2 will override it as needed:
(`production.js`文件作為基礎文件，其他 2 個文件將根據需要覆蓋它：)
  - `staging.js` will be loaded whenever the env variable `DS_ENV` is set to staging.
    (`staging.js` `DS_ENV`會加載當env 變量設置為暫存。)
  - `local.js` will be loaded if it exists.
    (`local.js`會被加載當它存在時。)

The following options must be set: (The used file will depend on the context)
(必須設置以下選項：（使用的文件將取決於上下文）)
  - `OAMUploaderApi` - The address of the [Uploader Api](https://github.com/hotosm/oam-uploader-api).
                       ([Uploader Api](https://github.com/hotosm/oam-uploader-api) 的地址)
  - `googleClient` - The client provided by google to use for the GDrive integration.
                     (谷哥提供的用戶端)
  - `googleDeveloperKey` - The developer key provided by google to use for the GDrive integration.
                     (谷哥提供的開發人員密鑰)
  - `OAMBrowserUrl` - The url of [OAM Browser](https://github.com/hotosm/oam-browser)
                     ([OAM Browser](https://github.com/hotosm/oam-browser) 的url)

Example:
``` 
module.exports = {
  OAMUploaderApi: 'http://localhost:4000',
  googleClient: 'somethingHERE.apps.googleusercontent.com',
  googleDeveloperKey: 'some long string',
  OAMBrowserUrl: 'https://beta.openaerialmap.org'
};
```
```
 cd oam-uploader/
 cd app/
 cd assets/
 cd scripts/
 cd config/
 nano production.js
 
 module.exports = {
  OAMUploaderApi: 'http://localhost:4000',
  googleClient: 'somethingHERE.apps.googleusercontent.com',
  googleDeveloperKey: 'some long string',
  OAMBrowserUrl: 'https://beta.openaerialmap.org'
};
 
```


#### Starting the app
    (啟動應用程序)

```
npm run serve
```
Compiles the sass files, javascript, and launches the server making the site available at `http://localhost:3000/`
The system will watch files and execute tasks whenever one of them changes.
The site will automatically refresh since it is bundled with livereload.

# Deployment
To prepare the app for deployment run:

```
npm run build
```
This will package the app and place all the contents in the `dist` directory.
The app can then be run by any web server.

## License
Oam Uploader is licensed under **BSD 3-Clause License**, see the [LICENSE](LICENSE) file for more details.
