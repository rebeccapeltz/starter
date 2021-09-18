---
description: >-
  You can enter credentials in plain text in an external config file. This is 
  not recommended for security reasons. Use environment variables to load
  credentials.
---

# Using External Config Files

While you should NOT enter your API\_SECRET as plain text in a sandbox file, you can create an external config file and reference `process.env.<environment variable name>`. You can even choose to enter the `api_secret`, `api_key,` and `cloud_name` as separate values. These can be filled in by exporting them to the command line if you are running the code from the command line or using SECRETS if you are running with the Green arrow.

We'll show an example where we export credentials form the command line, store references to credentials in an external module, and then require the module into index.js.

### Using a Config File To Store Credentials

You can add a Node.js file containing your credentials in plain text.  In that file you can use the NPM cloudinary package to read in the credentials and make them available to the SDK functions.  

Create a file  in the root of your project and name it **config.js**. In this file load the cloudinary package and then call the cloudinary config function passing it **API\_KEY, API\_SECRET,** and **CLOUD\_NAME**. Export this object with the name config. You can export both your configuration and the cloudinary library so that they are available to any module that requires configuration.

```javascript
// run config using credentials specified 
// in environment variables
// you can export these values in the Command Line Shell
const cloudinary = require('cloudinary').v2
const myconfig = cloudinary.config({
   cloud_name: process.env.cloud_name,
   api_key: process.env.api_key,
   api_secret: process.env.api_secret
});

// .module returns config and cloudinary references
module.exports = {
    config: myconfig,
    cloudinary: cloudinary
};
```

In your main **index.js** application file you can import this config as shown below.

```javascript
/** 
* cloudinary package has been installed - see package.json
* environment variables should be provided on command line
* click on Shell tab and export env variables 
export api_key=API_KEY
export api_secret=API_SECRET
export cloud_name=CLOUD_NAME
*/

// load cloudinary and config from external config file
const cloudinary = require('./config').cloudinary
const config = require('./config').config


// log the cloud name and API_KEY derived from the CLOUDINARY_URL to verify cloud location
// for security reasons, don't log API_SECRET
console.log(config.cloud_name)
console.log(config.api_key)

```

Before you run the code from the command line, export the 3 credentials.

```bash


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

Now run the code from the command line.

```bash
node index.js
```

If the application needs to access the values it can be done  as follows.

```javascript
const config = require('./config').config;
console.log(config)
console.log(config.cloud_name)

```

The code will log cloud name and api key to the console.

```bash
CLOUD_NAME
API_KEY
```

#### Note: When you run config using values assigned as we are doing above, the values will keep the case of the values you entered.  This differs from using cloudinary.config\(\) with the CLOUDINARY\_URL where values are lowercased.

#### Let's try it!

1. Click on the Shell tab at the bottom of the window
2. Export your 3 environment variables as shown above
3. Run `node index.js` 
4. Try exporting your actual credentials and executing the code

{% embed url="https://replit.com/@rpeltz/Cld-Nodejs-External-Config-File" caption="" %}

 [Return to Using the Repl.it Code Sandbox](using-external-config-files.md)



