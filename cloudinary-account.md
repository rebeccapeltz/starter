---
description: >-
  How to setup and use your Cloudinary credentials with a brief introduction to
  the Cloudinary Digital Asset Manager (DAM).
---

# Cloudinary Account

### Register For Account

You can register for a free account at Cloudinary [here](https://cloudinary.com/console) which is a link to the console.  Once you have registered and logged in, the link will take you to your credentials and other useful account information.

### Access Credentials

Once you have registered for an account you can access your credentials from the [**Console**](%20%20%20%20https://cloudinary.com/console) tab.  Here you will find your APIKEY, API\_SECRET and CLOUD\_NAME.  These credentials help to identify you \(API\_KEY\), your "password" \(API\_SECRET\), and where your assets are stored. \(CLOUD\_NAME\).  

**Note: you must protect you API\_SECRET by not including it in Front End Code or text that will get checked in to a public repository.  You will see that we load all of these credentials in environment variables so they are only available for the context of the program running.  Sometimes you will see API\_KEY and CLOUD\_NAME in code, but never API\_SECRET.**

#### Dashboard

You may see the Console referred to as the Dashboard.  The Dashboard is the first tab in the Cloudinary Digital Asset Manager \(DAM\) web page.

The best way to work with your credentials is using the API Environment variable `CLOUDINARY_URL`. When you click on Copy to clipboard, you add this you your clipboard memory: `CLOUDINARY_URL://cloudinary://<API_KEY>:<API_SECRET>@<CLOUD_NAME>`

The `<>` names will be filled with your credentials.  The Cloudinary SDK provides a `config()` function that can parse out these values.  See how to do this in notes on [`REPL.it Code Sandbox`](node.js/using-the-repl.it-code-sandbox/).

![](.gitbook/assets/dashboard.jpg)



[Return to Guide](./)

