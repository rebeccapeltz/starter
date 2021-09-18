---
description: 'Upload image, raw and video files.'
---

# Upload

## Upload 

There are many options available to upload images, raw and video assets. You'll find Sandboxes for both on this page. The basic upload is very similar for this starter. You supply a source for your media, which in this case will be a remote file. You will need to also supply a `resource_type` if you are uploading a video or raw file. The default `resource_type` is `image` and will include for comparison.

Because we are not explicitly providing a unique public id or indicating that the public id be assigned a file name, we'll get a 20 character random string for the public id.

To run these scripts from inside this page

1. Click on the Shell tab
2. Export your Cloudinary URL on the command line
3. Execute `node index.js` on the command line
4. Click on the `secure_url` in the response to see the deliver the image to the browser

#### Upload Image File

{% embed url="https://replit.com/@rpeltz/Cld-Nodejs-Image-Upload" caption="" %}

#### Upload Raw File

{% embed url="https://replit.com/@rpeltz/Cld-Nodejs-Raw-Upload" caption="" %}

#### Upload Video File

{% embed url="https://replit.com/@rpeltz/Cld-Nodejs-Video-Upload" caption="" %}

[Node Setup](./)

