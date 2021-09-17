---
description: >-
  You can enter credentials in plain text in an external config file. We won't
  be using this with REPL.IT but it may be of use.
---

# Using External Config Files

### Using a Config File To Store Credentials

You can add a Node.js file containing your credentials in plain text.  In that file you can use the NPM cloudinary package to read in the credentials and make them available to the SDK functions.  It is **not good practice to leave your API\_SECRET in a code sandbox file**, but you may want to use this in your application so it is presented here as an option.

Create a file  in the root of your project and name it **config.js**. In this file load the cloudinary package and then call the cloudinary config function passing it **APIKEY, API\_SECRET,** and **CLOUD\_NAME**. Export this object with the name config.

```javascript
//filename: config.js
const cloudinary = require('cloudinary').v2
const myconfig = cloudinary.config({
   cloud_name: '<cloud name>',
   api_key: '<api key>',
   api_secret: '<api secret>',
   secure: true
});

module.exports = {
    config: myconfig
};
```

The results of both functions above are the same.  A config object is exported for used by the Cloudinary Node.js SDK.

In your main **index.js** application file you can import this config as shown below.

```javascript
const config = require('./config').config;
console.log(config)
```

The code above will log this to the console.

```bash
{
  cloud_name: '<cloud name>',
  api_key: '<api key>',
  api_secret: '<api secret>',
  secure: true
}
```

If the application needs to access the values it can be done  as follows.

```javascript
const config = require('./config').config;
console.log(config)
console.log(config.cloud_name)
```

The code above will log this to the console.

```bash
<cloud name>
```

 [Return to Using the Repl.it Code Sandbox](using-external-config-files.md)

