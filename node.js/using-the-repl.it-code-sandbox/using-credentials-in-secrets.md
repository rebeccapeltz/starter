---
description: Repl.it provides a SECRET user interface to store environment variables.
---

# Using Credentials in SECRETS

They code presented here will work the same for an .env file as it does for the SECRETS storage that repl.it uses.

When you click on the lock icon in REPL.IT, you will have an opportunity to enter CLOUDINARY\_URL as the "key" and the full URL as the "value" into the form. 

![REPL.IT Secret for Credentials](../../.gitbook/assets/secrets.jpg)

If you were working in an environment that doesn't capture **SECRETS** as shown above, you would create a **.env** file and add **CLOUDINARY\_URL**_=_**cloudinary://API\_KEY:API\_SECRET@CLOUD\_NAME.**   **Best Practice:** If you do create a **.env** file in a project, be sure to add it to a **.gitignore** file so that it doesn't end up in **GitHub**. 

**Making Environment Variables Available to Code**

Environment variables that are stored in **SECRETS** or and **.env** file must be extracted so that they are available to the application context as process.env.&lt;environment variable&gt;.  You can use the NPM **dotenv** package to do this.  The **dotenv** config\(\) function will extract and export  environment variables stored in **SECRETS** or a **.env** file.

First you must install .dotenv package.  If we were working in the command shell the install would look like this:

```bash
npm install dotenv
```

However, when working in REPL.IT, we use the package manager they provide.



When you use environment variables your index.js file will look like the code below.

```javascript
contains your API_SECRET
require('dotenv').config()

//the cloudinary library contains Node.js code wrapping all SDK functions and utilities - you only need this if you are not using the external config file for credentials
const cloudinary = require('cloudinary').v2

//log the cloudname derived from the CLOUDINARY_URL to verify cloud location
console.log(cloudinary.config().cloud_name)
```

If my environment variable is **CLOUDINARY\_URL**_=_**cloudinary://API\_KEY:API\_SECRET@CLOUD\_NAME,**  the code above will log this to the console. 

```javascript
cloud_name
```

The **cloudinary config\(\)** function parses the CLOUDINARY URL to allow access to individual elements of it.

We'll be using environment variables in all of the code sand boxes for this startup guide.  You can practice adding your credentials as environment variables in the REPL.IT sandbox below. Start by exporting your CLOUDINARY\_URL in the **Shell**.  Then run the index.js by  entering the following command in the shell.

```bash
node index.js
```

#### 

#### Forking the Code Sandbox

xxx you need to read the data in e

You will want to use an NPM package named **dotenv** to read the **process.env.CLOUDINARY\_URL** from your application context.

Install the [dotenv](https://www.npmjs.com/package/dotenv) library to enable access to environment variables in your code.  If we were working in the command shell the install would look like this:

```bash
npm install dotenv
```

However, when working in REPL.IT, we use the package manager they provide.



In your application, you execute the following command to read the environment variables into your application.

```javascript
require('dotenv').config
```



If you want to use the **green arrow at the top of the sandbox** to run the code, 

![The Green arrow can run the index.js.](../../.gitbook/assets/green-arrow.jpg)

Click on **open in replit.  You will see a new window like this**

![Opening and embedded replit code sandbox](../../.gitbook/assets/2021-09-10_17-11-29.png)

Next you should click on the "**Fork**" button in the upper right corner.  You will need to create a free account on repl.it to fork it.

Next add your CLOUDINARY\_URL to the Secrets

![Click on the Lock](../../.gitbook/assets/secrets-forked.jpg)

Click on the Lock icon to open Secrets and enter the key \(**CLOUDINARY\_URL**\) and the value \(**cloudinary://API\_KEY:API\_SECRET@CLOUD\_NAME\).**

![Entering Credentials as Secret](../../.gitbook/assets/secret-value.jpg)

**Now click on the green button to run the index.js script.**

![Using green button to run the script](../../.gitbook/assets/cloud_name.jpg)

**NOTE: If you share the URL to your own REPL.IT  sandbox and it contains a secret, no one will be able to see your secrets.  They are only visible to the person who created them.  The person you share with will need to fork the sandbox just like you did above.**

[Extra: Using External Config ](../using-external-config-files.md)

