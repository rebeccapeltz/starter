---
description: Repl.it provides a SECRET user interface to store environment variables.
---

# Using Credentials in SECRETS

They code and process presented here will work the same for an .env file as it does for the SECRETS storage that repl.it uses.   You will need to [create an account on Repl.it](https://replit.com/signup?from=landing) in order to use SECRETS.

### Adding SECRETS 

When you click on the lock icon in REPL.IT, you will have an opportunity to enter CLOUDINARY\_URL as the "key" and the full URL as the "value" into the form. 

![REPL.IT Secret for Credentials](../../.gitbook/assets/secrets.jpg)

If you were working in an environment that doesn't capture **SECRETS** as shown above, you would create a **.env** file and add **CLOUDINARY\_URL**_=_**cloudinary://API\_KEY:API\_SECRET@CLOUD\_NAME.**   **Best Practice:** If you do create a **.env** file in a project, be sure to add it to a **.gitignore** file so that it doesn't end up in your public repository storage. 

### **Making Environment Variables Available to Code**

Environment variables that are stored in **SECRETS** or an **.env** file must be extracted so that they are available to the application context as process.env.&lt;environment variable&gt;.  You can use the NPM **dotenv** package to do this.  The **dotenv** config\(\) function will extract and export  environment variables stored in **SECRETS** or an **.env** file.

First you must install .dotenv package.  If we were working in the command shell the install would look like this:

```bash
npm install dotenv
```

However, when working in REPL.IT, we use the package manager they provide. First you would click on the **package** icon on the far left. Next you search for the package you need and then click a plus \(+\) to install the package, or the garbage icon to remove it.  Once installed, you'll see it in the package.json.

![Using the repl.it Package Manager](../../.gitbook/assets/install-packages.jpg)

### Using dotenv and cloudinary.config\(\)

When you use environment variables your index.js file will look like the code below.  Before you can call cloudinary.config\(\), you need to extract the environment variables, in this case the Cloudinary URL, from SECRETS.

```javascript
// extract environmnet variables and put into 
// process.env.CLOUDINARY_URL
require('dotenv').config()

// the cloudinary library contains Node.js code wrapping all API
const cloudinary = require('cloudinary').v2

// log the cloud name derived from the CLOUDINARY_URL 
// to verify cloud location
console.log(cloudinary.config().cloud_name)
```

If your environment variable is **CLOUDINARY\_URL**_=_**cloudinary://API\_KEY:API\_SECRET@CLOUD\_NAME,**  the code above will log this to the console. 

```javascript
cloud_name
```

The `cloudinary.config()` function parses the CLOUDINARY URL to allow access to individual elements of it.

### Forking the Code Sandbox

When you use SECRETS, the Cloudinary URL will not be available to scripts called from the command line.

Instead of running the script from the command line, you can execute it  pressing the green arrow button.  However, before you can see the green arrow button at the top center of the web page, you need to create a free account on Repl.it, fork the code and add your Cloudinary URL to SECRETS.  

The images below walk you through the steps to get from an embedded sandbox to a forked Sandbox with your credentials hidden in SECRETS.

#### 1. The Green Button and Open in replit

![The Green arrow can run the index.js.](../../.gitbook/assets/green-arrow.jpg)

Click on **open in replit.  You will see a new window like this**

![Opening and embedded replit code sandbox](../../.gitbook/assets/2021-09-10_17-11-29.png)

#### 2. Fork It

Next you should click on the "**Fork**" button in the upper right corner.  You will need to create a free account on repl.it to fork it.

#### 3. Add Secrets

Next add your CLOUDINARY\_URL to the Secrets



![Click on the Lock](../../.gitbook/assets/secrets-forked.jpg)

Click on the Lock icon to open Secrets and enter the key \(**CLOUDINARY\_URL**\) and the value \(**cloudinary://API\_KEY:API\_SECRET@CLOUD\_NAME\).**

![Entering Credentials as Secret](../../.gitbook/assets/secret-value.jpg)

#### 4. Press Green Button and Find Output in Console

Now click on the green button to run the index.js script.

![Using green button to run the script](../../.gitbook/assets/cloud_name.jpg)

\*\*\*\*

**Let's Try It**

When you click on the Green button in the sandbox below, the code will run but there will be no environment variables set up, so your code will return undefined. You need to fork the code and add your SECRETS environment variables to successfully run the code.

1. Login to your replit account
2. Click on the Green arrow and nothing happens
3. Click on Open in replit
4. You'll open the sandbox in a new window but the green arrow will have turned black
5. You can view the code but you can't run it using the arrow
6. At this point, click on Fork in the right hand corner
7. Replit will create a copy of the sandbox in under your account
8. Add your Cloudinary URL to SECRETS and you can use `CLOUDINARY_URL=cloudinary://API_KEY:API_SECRET@CLOUD_NAME` for testing
9. Packages will normally be setup in package.json, but you can check and add any additional packages using the Package Manager
10. Click on the Green arrow to execute the code  using Node.js in **index.js**
11. You should see the output under the console tab at the bottom of the page

{% embed url="https://replit.com/@rpeltz/Cld-Nodejs-Config-Using-Secrets-for-env" caption="Embedded Sandbox" %}

**NOTE: If you share the URL to your own REPL.IT  sandbox and it contains a secret, no one will be able to see your secrets.  They are only visible to the person who created them.  The person you share with will need to fork the sandbox just like you did above.**

[Return to REPL.IT Code Sandbox](./)

