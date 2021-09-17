---
description: >-
  How to export credentials from the command line and practice doing it with a
  Repl.it sandbox.
---

# Using Credentials on the Command Line



The CLOUDINARY\_URL contains all of the credentials you need to provide security \(APIKEY\), identify yourself \(API\_KEY\) and identify your cloud \(CLOUD\_NAME\).  They are capitalized in the URL but you'll reference them as lowercase in your code.

You can locate the command shell in the sandbox and execute the following command to add CLOUDINARY\_URL to your application context. Substitute the CLOUDINARY\_URL from your Cloudinary dashboard to access your cloud programatically.  Notice that the export contains a Key/Value pair where CLOUDINARY\_URL is the key and cloudinary://APIKEY:API\_SECRET@CLOUDNAME is the value.

#### Export Your Cloudinary URL in the Command Line

```bash
export CLOUDINARY_URL=cloudinary://API_KEY:API_SECRET@CLOUD_NAME
echo $LCOUDINARY_URL
```

The command above will make the CLOUDINARY\_URL accessible in your code by referencing **process.env.CLOUDINARY\_URL**.  If you access the full URL using process.env, you will leave it capitalized.

```javascript
console.log(process.env.CLOUDINARY_URL)
```

The Cloudinary config\(\) function looks for this environment variable.  It then parses the CLOUDINARY\_URL into separately accessible values like **api\_key**, **api\_secret**, and **cloud\_name**.  In the code below we log the api\_key and cloud\_name.

_We must first install the NPM cloudinary library in order to use the cloudinary.config\(\) function._

```bash
npm install cloudinary
```

With that in place we can log our public credentials.

```javascript
const cloudinary = require('cloudinary').v2
const configuration = cloudinary.config()

console.log(configuration.cloud_name)
console.log(configuration.api_key)
```

### **Try It Out!**

An embedded Repl.it sandbox is shown below.  

1. Click on the tab to take you to the Command line Shell
2. Locate the Command Line at the bottom of the embedded window
3. We have already added the Cloudinary package so **you don't need to run** the NPM install command.
4. Export your Cloudinary Url in the command line by entering `export CLOUDINARY_URL=cloudinary://API_KEY:API_SECRET@CLOUD_NAME`
5. Run the script form the command line by entering `node index.js` 
6. You should see what's shown in the image below.
7. Now try exporting the Cloudinary URL from your account and executing the script.

![Export Credentials from Command Line](../../.gitbook/assets/cl-credentials.jpg)

Code Sandbox to Practice Exporting Credentials on the Command Line.

{% embed url="https://replit.com/@rpeltz/Cld-Nodejs-Config-CL" %}

[REPL.IT Code Sandbox](./)

