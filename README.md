# PLEASE READ THIS SECTION
## This is a heavily modified version of hat.sh designed to make it integrate better with desktop environments. If you want to just use the webapp, please use the regular repository [here](https://github.com/sh-dv/hat.sh), because this will likely not run the way you would like it to on your web browser.

### I'll try to update this with any updates sh-dev puts out on the 1.5 branch, and intend to port v2 to Electron once it is officially out of beta.

<br>
<hr>

<p align="center">
  <a href="#" rel="noopener">
 <img src="https://i.imgur.com/F8nNzHi.png"></a>
</p>

<a href="https://hat.sh" style="color:#000"><h3 align="center">https://v1.hat.sh</h3></a>

<div align="center">

  [![Status](https://img.shields.io/badge/status-active-success.svg)](#)
  [![Build](https://travis-ci.org/sh-dv/hat.sh.svg?branch=master)](https://travis-ci.org/sh-dv/hat.sh)
  [![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](#)

<a href="https://www.producthunt.com/posts/hat-sh?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-hat-sh" target="_blank">
    <img src="https://api.producthunt.com/widgets/embed-image/v1/top-post-badge.svg?post_id=157956&theme=dark&period=daily" alt="hat.sh - Free, fast, secure and serverless file encryption | Product Hunt Embed" width="250px"/>
</a>
<br>
<a href="https://www.privacytools.io/software/encryption-tools/" target="_blank">
    <img src="https://i.imgur.com/Euyd1ap.png" alt="hat.sh - Free, fast, secure and serverless file encryption" width="250px"/>
</a>

</div>

---


[hat.sh](https://hat.sh) is a  javascript app that provides secure file encryption using the [AES-256-GCM](https://www.w3.org/TR/WebCryptoAPI/#aes-gcm) algorithm from [WebCryptoAPI](https://www.w3.org/TR/WebCryptoAPI/#aes-gcm) provided by your browser. it was coded following the WebCrypto [Documentations](https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto).

 It's **fast**, **secure** and **Serverless**, the app never uploads the files to the server.
 
in a small amount of code the app can encrypt any **type** of files at any **size** within seconds.
 
To use the app all you have to do is **Browse** a file,  **Type** a Decryption Key or **Generate** one through our secure key generator. and your encrypted file is ready to download.



## Requirements
[NodeJS and NPM](https://www.npmjs.com/get-npm)

[Browserify](http://browserify.org/#install) which lets you require('modules') in the browser by bundling up all of your dependencies.

<hr>

## Installation

Download or clone the repository

 

    $ git clone https://github.com/deevonstutter/hat.sh.git hat.sh

go to the app directory

    cd [app directory]

now run 
    
    npm run full-build
which will install all the node dependencies and build the Browserify bundle.
At this point you can run the electron 

<br>

## NEW SCRIPTS
Though this is mostly for electron support, I do have some scripts that can be run from the root directory as well.
Also please keep in mind these scripts were built for **WINDOWS ONLY**.
<hr>

    npm run build
This will run the Browserify build process and copy the resulting `bundle.js` to the Electron directory.
<hr>

    npm run full-build
This is really just for initializing your build environment.
<hr>

    npm run e-serve
This will run the Electron instance.

<hr>

## Browser Compatibility
We officially support the last two versions of every major browser. Specifically, we test on the following 
-   **Chrome**  on Windows, macOS, and Linux , IOS, Android
-   **Firefox**  on Windows, macOS, and Linux
-   **Safari**  on iOS and macOS
-   **Edge**  on Windows
-   **IE 11**  on Windows

for more info see [WebCryptoAPI](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API) home page
![enter image description here](https://i.imgur.com/hJveblf.png)


## Crypto Examples

#### AES-GCM - generateKey
```javascript
  window.crypto.subtle.generateKey(
    {
      name: "AES-GCM",
      length: 256,
    },
    true,
    ["encrypt", "decrypt"]
  )
.then(function(key){
    console.log(key);
})
.catch(function(err){
    console.error(err);
});
```
#### AES-GCM - importKey
```javascript
function importSecretKey(rawKey) {
    return window.crypto.subtle.importKey(
      "raw",
      rawKey,
      "AES-GCM",
      true,
      ["encrypt", "decrypt"]
    );
  }
.then(function(key){
    console.log(key);
})
.catch(function(err){
    console.error(err);
});
```
#### AES-GCM - exportKey
```javascript
async function exportCryptoKey(key) {
    const exported = await window.crypto.subtle.exportKey(
      "raw",
      key
    )
.then(function(keydata){
    console.log(keydata);
})
.catch(function(err){
    console.error(err);
});
```
#### AES-GCM - encrypt
```javascript
async function encryptMessage(key) {
    let encoded = getMessageEncoding();
    // The iv must never be reused with a given key.
    iv = window.crypto.getRandomValues(new Uint8Array(12));
    ciphertext = await window.crypto.subtle.encrypt(
            {
                name: "AES-GCM",
                iv: iv
            },
            key,
            encoded
        )
        .then(function (encrypted) {
            console.log(new Uint8Array(encrypted));
        })
        .catch(function (err) {
            console.error(err);
        });
}
```
#### AES-GCM - decrypt
```javascript
async function decryptMessage(key) {
    let encoded = getMessageEncoding();
    let decrypted = await window.crypto.subtle.decrypt({
            name: "AES-GCM",
            iv: iv
        },
        key,
        ciphertext
       )
       .then(function (decrypted) {
            console.log(new Uint8Array(encrypted));
        })
        .catch(function (err) {
            console.error(err);
        });
}
```
## Credits
[zxcvbn.js](https://github.com/dropbox/zxcvbn) for Smart Password Strength Estimation

[bootstrap](https://github.com/twbs/bootstrap) for the responsive css layout

[font-awesome](https://github.com/FortAwesome/Font-Awesome) for the icons

## License
[Copyright (c) 2019 sh-dv](https://github.com/sh-dv/hat.sh/blob/master/LICENSE)
