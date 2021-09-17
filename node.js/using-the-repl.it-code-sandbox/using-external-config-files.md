---
description: >-
  You can enter credentials in plain text in an external config file. This is
  not recommended for security reasons.
---

# Using External Config Files

While you should NOT enter your API\_SECRET as plain text in a sandbox file, you can create an external config file and reference process.env.&lt;environment variable name&gt;.  You can even choose to enter the api\_secret, api\_key, and cloud\_name as separate values.  These can be filled in by exporting to them to the command line if you are running the code form the command line or using SECRETS if you are running with the Green arrow.

We'll show an example where we run the from Command Line and store references to credentials in an external module which we import into index.js

### Using a Config File To Store Credentials

You can add a Node.js file containing your credentials in plain text.  In that file you can use the NPM cloudinary package to read in the credentials and make them available to the SDK functions. 

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

