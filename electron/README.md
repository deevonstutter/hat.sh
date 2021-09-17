  
<p align="center">
  <a href="#" rel="noopener">
 <img src="https://i.imgur.com/F8nNzHi.png"></a>
</p>

<h3 align="center">Hat.sh</h3>

<div align="center">

  [![Status](https://img.shields.io/badge/status-active-success.svg)](#)
  [![https://github.com/sh-dv/hat.sh](https://travis-ci.org/sh-dv/hat.sh.svg?branch=master)](#)
  [![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](#)
  <p align="center">
    <a href="https://www.producthunt.com/posts/hat-sh?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-hat-sh" target="_blank">
    <img src="https://api.producthunt.com/widgets/embed-image/v1/top-post-badge.svg?post_id=157956&theme=dark&period=daily" alt="hat.sh - Free, fast, secure and serverless file encryption | Product Hunt Embed" width="250px"/>
    </a>
  </p>

</div>

---


[hat.sh](https://hat.sh) is a  javascript app that provides secure file encryption using the [AES-256-GCM](https://www.w3.org/TR/WebCryptoAPI/#aes-gcm) algorithm from [WebCryptoAPI](https://www.w3.org/TR/WebCryptoAPI/#aes-gcm) provided by your browser. it was coded following the WebCrypto [Documentations](https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto) .

 It's **fast**, **secure** and **Serverless**, the app never uploads the files to the server.
 
in a small amount of code the app can encrypt any **type** of files at any **size** within seconds.
 
To use the app all you have to do is **Browse** a file,  **Type** a Decryption Key or **Generate** one through our secure key generator. and your encrypted file is ready to download.

## Installation using electron

Download or clone the repository

 

    $ git clone https://github.com/deevonstutter/hat.sh.git hat.sh

go to the app electron directory

    cd [app directory]/elctron

open terminal and install the node modules that are in the package.json file

    sudo npm i
after the packages are installed just run the app

    npm start
to package the app for multiple os systems (mac,win,linux) :

    npm run package-[os name] 

## *NOTE:*
This is an edited version of the regular hat.sh. I've added some npm scripts that make it a bit easier to directly deal with electron. These are as follows:
 <hr>   

    npm run serve
This will build the electron package **FOR WINDOWS** and then run it.
<hr>

    npm run build
I made this one mostly for convenience, it will build the `app.js` script via Browserify and copy the resulting `bundle.js` to the proper directory to be read by Electron.

## Some Other Useful Info
Because this is built with Browserify, some Node and Electron dependencies cannot be directly used as normal.
For example, direct filesystem access must be done using
```js
const fs = window.require('fs');
```
rather than 
```js
const fs = require('fs');
```
because Browserify will strip the Node code and replace it with something for, well, browsers. 
This will unfortunately break IntelliSense in VS Code, so if you choose to use require statements, please make sure you add the `window.` to the require statement before you commit.



## Credits
[zxcvbn.js](https://github.com/dropbox/zxcvbn) for Smart Password Strength Estimation

[bootstrap](https://github.com/twbs/bootstrap) for the responsive css layout

[font-awesome](https://github.com/FortAwesome/Font-Awesome) for the icons

## License
[Copyright (c) 2019 sh-dv](https://github.com/sh-dv/hat.sh/blob/master/LICENSE)
