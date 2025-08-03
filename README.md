## Static Site Server
Setup a basic linux server and configure it to serve a static site.

The goal of this project is to help you understand the basics of setting up a web server using a basic static site served using `Nginx`. You will also learn how to use `rsync` to deploy your changes to the server.

### Requirements
Here are the requirements for this project:

* Register and setup a remote linux server on any provider e.g. a simple droplet on DigitalOcean which gives you $200 in free credits with the link. Alternatively, use AWS or any other provider.
* Make sure that you can connect to your server using SSH.
* Install and configure nginx to serve a static site.
* Create a simple webpage with basic HTML, CSS and image files.
* Use rsync to update a remote server with a local static site.
* If you have a domain name, point it to your server and serve your static site from there. Alternatively, set up your nginx server to serve the static site from the server’s IP address.
You can write a script deploy.sh which when you run will use rsync to sync your static site to the server.

Once you have completed the project, you should have a basic understanding of how to setup a web server using a basic static site served using `Nginx`. You should also have a basic understanding of how to use `rsync` to deploy your changes to the server.


## Image Processing Service
This project involves creating a backend system for an image processing service similar to Cloudinary. The service will allow users to upload images, perform various transformations, and retrieve images in different formats. The system will feature user authentication, image upload, transformation operations, and efficient retrieval mechanisms.

### Requirements
Here is the list of features that you should implement in this project:

#### User Authentication
* Sign-Up: Allow users to create an account.
* Log-In: Allow users to log into their account.
* JWT Authentication: Secure endpoints using JWTs for authenticated access.
  
#### Image Management
* Upload Image: Allow users to upload images.
* Transform Image: Allow users to perform various transformations (resize, crop, rotate, watermark etc.).
* Retrieve Image: Allow users to retrieve a saved image in different formats.
* List Images: List all uploaded images by the user with metadata.
  
#### Image Transformation
Here is the list of transformations that you can implement:
* Resize
* Crop
* Rotate
* Watermark
* Flip
* Mirror
* Compress
* Change format (JPEG, PNG, etc.)
* Apply filters (grayscale, sepia, etc.)




