---
layout: post
title:  "[Node/Express/EJS] Adding local scripts, css, to EJS views "
date:   2019-09-21
excerpt: " "
tag:
- javascript
- Nodejs
- Express
- import local scripts
comments: true
feature: https://images.unsplash.com/photo-1467320424268-f91a16cf7c77?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80
category: [ Javascript ]
---

The examples here are only written to help the understanding of the above topic, and details have been omitted. It is possible for these examples to lack of individual features regarding Node, Express and EJS. Please do keep this in mind before proceeding! Thank you.

Let's assume you have a project with the following directory structure in this directory `~/Documents/Proejcts/project_test1/.`

```
project_test1
  app.js
  /public
    /stylesheets
      style.css
  /utils
    index.js
  /views
    home.ejs
  ... etc
    
```

In order to use the local files from the project directory, include the following middleware early in your `app.js`.

```js
app.use(express.static(path.join(__dirname)))
```

- [**app**](https://expressjs.com/en/api.html) - app object is an instance of Express server
- [**app.use**](https://expressjs.com/en/guide/using-middleware.html) - adds middleware to the **middleware stack**
- [**express.static**](https://expressjs.com/en/starter/static-files.html) - built-in middleware function in express. 
- [**__dirname**](https://nodejs.org/docs/latest/api/modules.html#modules_dirname) - built in node js variable that stores the directory name of current module in string type.

Now add the following script or link tag in your `home.ejs`. The ejs file will now load local script and css files. 

```ejs
// For local script import
<script type='text/javascript' src='/utils/index.js'></script>
// For local css import
<link rel='stylesheet' href='/public/stylesheets/style.css'
```
