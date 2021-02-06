# NodeJS Getting Started

This document is to get you started in modern, 2021 [Node.js](https://nodejs.org)  and [NPM](https://www.npmjs.com/) ecosystem. Unlike regular javascripts that run on your browsers (front-end), NodeJs runs your JS code on your machine or servers (back-end). This backend features enables node.js to have many functionalities that client-side (browser) js doesn't have, including:
- file access
- start as a server
- low level networking
- other OS interaction 
## NodeJS Installation

Install Chocolatey https://chocolatey.org/install
```
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

Run a cmd in administrator mode, and run the following commands:

```
choco install nodejs -y
npm i express
npm i react
```
### Some NPM commands

global versus local package

    npm ls -g --depth 0

npm environment is file directory based, which means, an "environment" is self-contained in a directory.

    package.json
    node_modules

The `npm` command allows you to manage your npm system locally. Try `npm -h` to view help. The other common usage includes:

    npm i xxx  // to install package xxx
    npm update // to update

### Some Node commands

Check out your NodeJs version, See the version history [here](https://nodejs.org/en/download/releases/).
    
    node -v
    node -h // help output

Run a js file

    node xxx.js

## Server side vs Client Side vs Command Line.

On the internet, Javascript can be used in both front-end and back-end code. What does it mean to be client side / front-end code?

Javascript can also be used to create an executable to be run on your desktop or servers.

### Client Side

Client side codes get loaded into your browser when you hit the site, and they run in your browser. The front-end code is very limited in terms of what they can do as they run in the browsers' sandbox.

A popular client side framework is [React](https://reactjs.org/). The other popular front-end frameworks include [Vue.js](https://vuejs.org/) and [Angular](https://angular.io/). You can see the popularity on [Top Front-End Frameworks in 2020](https://existek.com/blog/top-front-end-frameworks-2020/)  

### Server Side

Server side codes, on the other hand, are very powerful, just like Java or Python. They run on the server so they are not "exposed". They only get called through URLs / web services. 

The most popular way to create the web service is through [Express](https://expressjs.com/).
### Executable

Executable can be either command line tool or desktop apps. One tool to make an exe is [PKG](https://www.npmjs.com/package/pkg). More detail below in Special Topic->Packaging.

These are some [JavaScript Frameworks for Desktop Apps](https://brainhub.eu/blog/javascript-frameworks-for-desktop-apps/)

## NodeJS Tutorials
### Hello World

    mkdir test
    cd test
    npm init -y
    // view package.json file. 
    echo console.log("hello world!"); > index.js
    // run node index.js

### Parameter from Command line

    console.log(process.argv);

    var a = process.argv.slice(2);
    console.log(a);
    console.log(a.join(" "));

    for (i in a) {
        console.log(i);
    }

Note that the output between "node index.js" and "index.exe" are identical. This indicates that "pkg" is just a wrapper.

### JSON & File I/O

Json (JavaScript Object Notation) is the preferred message format. It is natively supported by Javascript, therefore all the modern web pages can consume Json without formatting any conversion.

    var fs = require('fs');
    var jsonData = JSON.stringify(arr);
    fs.writeFileSync("arr.json",jsonData);

    var contents = fs.readFileSync("arr.json");
    var arr_new = JSON.parse(contents);

### functions and modules in JS

in lib.js

    function add(a,b) {
        return a+b+1;
    };

    module.exports = {add}
    // or exports.add = add;


in caller.js

    function add(a,b) {
        return a+b;
    };
    const lib = require("./lib");
    console.log(lib.add(1,2));
    console.log(add(1,2));

## NPM Package Samples

Explore some NPM packages
### Sample 1. Weather

Search for ``npm weather-js`` and pick [weather-js](https://www.npmjs.com/package/weather-js).

Install then copy&paste the sample code. Run the sample code, then add the following code to get the temp of the first city returned.

    console.log(result[0].current.temperature);

### Sample 2. Reading Excel File

Search for ``npm excel`` and pick [read-excel-file](https://www.npmjs.com/package/read-excel-file).

### Express

We can use [Express](https://expressjs.com/) for the back-end API server. They have this [Hello World example](https://expressjs.com/en/starter/hello-world.html).

Add the following to pass in an argument

    .get('/:arg1', function (req, res) {
      res.send('Hello World '+req.params.arg1)
    })

Add the following to implement a power function

#### Excel

Use Excel as a client. 

Below is a simple implementation on Excel 2010 (on which [WebService() function](https://support.office.com/en-us/article/webservice-function-0546a35a-ecc6-4739-aed7-c0b7ce1562c4) is not supported yet.

```
Public Function Webservice(url)
    Set XML = CreateObject("MSXML2.XMLHTTP")
    XML.Open "GET", url, False
    XML.Send
    Webservice = XML.responseText
End Function

```

### axios

Use NodeJS as the client

    https://www.npmjs.com/package/axios


Sample code:

```
const axios = require('axios');
 
axios.get('http://localhost:3000/')
  .then(function (response) {
    // console.log(response);
    console.log(response.data);
  })
  .catch(function (error) {
    console.log(error);
  });
```

## Special Topics

### NPM's Package Lock

https://docs.npmjs.com/files/package-lock.json
### Packaging

PKG : https://www.npmjs.com/package/pkg

This command line interface enables you to package your Node.js project into an executable that can be run even on devices without Node.js installed.

Note that this is a "global" installation. This way, we don't have to install this in every project.

Add the following two lines in package.json:

    "start": "node index.js",
    "build": "pkg index.js --target node10-win-x64",

then you can build by running "npm run build", or you can run something like this directly:

    pkg loop.js -t node6-win -o test.exe

### Registry

[Verdaccio](https://verdaccio.org/docs/en/what-is-verdaccio) is a lightweight private npm proxy registry built in Node.js


### Spread syntax 

Spread syntax on [mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

    var numArray = [3,6,24,67,2,33];
    Math.max(...numArray);

### Promise

Most of the Javascript libraries have been using call-back functions, a very good practice that made programs non-blocking and responsive. However the drawback could be that when you need to accomplish a series of functions, your code will look ridiculous as each following action will need to be in a callback function from previous one. This changed when JS officially introduced [promises](https://developers.google.com/web/fundamentals/primers/promises)

