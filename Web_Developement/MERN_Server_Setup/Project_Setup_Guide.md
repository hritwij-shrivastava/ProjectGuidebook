# Project Setup README

This comprehensive README provides step-by-step instructions for setting up the required software and configurations for your project. Please follow these steps carefully to ensure a successful setup.

---

## Table of Contents

1. [Install LibreOffice](#1-install-libreoffice)
2. [Install GraphicsMagick](#2-install-graphicsmagick)
3. [Install GhostScript](#3-install-ghostscript)
4. [Install ImageMagick](#4-install-imagemagick)
5. [Nginx SSL Certificate](#5-nginx-ssl-certificate)
6. [Configure Git in Ubuntu](#6-configure-git-in-ubuntu)
7. [Final Node.js Deployment](#7-final-nodejs-deployment)
8. [Final React Code](#8-final-react-code)
9. [Install Node.js on Ubuntu 18.04 LTS AWS](#9-install-nodejs-on-ubuntu-1804-lts-aws)
10. [Install PM2](#10-install-pm2)

---

## 1. Install LibreOffice

To install LibreOffice on your Ubuntu 16.04 system, follow these steps:

- Open your terminal and execute the following commands:

```bash
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update
sudo apt install libreoffice
```

[Detailed Installation Guide](https://www.liquidweb.com/kb/installing-libreoffice-on-ubuntu-16-04/)

---

## 2. Install GraphicsMagick

GraphicsMagick is essential for image processing. Follow these steps to install GraphicsMagick and its dependencies:

```bash
sudo apt-get update
sudo apt-get install libpng12-0 libjpeg-dev ghostscript libtiff5-dev libfreetype6

# Download GraphicsMagick
wget ftp://ftp.graphicsmagick.org/pub/GraphicsMagick/1.3/GraphicsMagick-1.3.26.tar.gz

# Extract and install GraphicsMagick
tar xzvf GraphicsMagick-1.3.26.tar.gz
cd GraphicsMagick-1.3.26
./configure
sudo apt-get install build-essential
./configure
make
sudo make install

# Verify the installation
gm version
```

[Detailed Installation Guide](https://gist.github.com/neoneye/00fad388e38f5b0361f66cc1a3b2f57e)

---

## 3. Install GhostScript

GhostScript is required for handling PDFs. Install it with the following commands:

```bash
sudo apt-get update
sudo apt -y install ghostscript
```

---

## 4. Install ImageMagick

ImageMagick is another tool for image manipulation. Install it and configure PDF policy:

```bash
sudo apt update
sudo apt install imagemagick
identify -version

# Configure ImageMagick policy
sudo vim /etc/ImageMagick-6/policy.xml

# Replace this line: <policy domain="coder" rights="none" pattern="PDF" />
# With: <policy domain="coder" rights="read|write" pattern="PDF" />
```

---

## 5. Nginx SSL Certificate

Secure your Nginx server with a Let's Encrypt SSL certificate by following this guide:

[How to Secure Nginx with Let's Encrypt on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-18-04)

```bash
sudo nano /etc/nginx/sites-available/default
```

---

## 6. Configure Git in Ubuntu

Set up your Git configuration with your name and email:

```bash
git --version
git config --global user.name "hritwij-shrivastava"
git config --global user.email "hritwij01shrivastava@gmail.com"
git config --list
git clone https://github.com/hritwij-shrivastava/Mern-Stack-Portfolio-Website
```

---

## 7. Final Node.js Deployment

Set up a Jenkins job named "Mern-Stack-Portfolio-Website" and configure it as follows:

1. Add the GitHub repository URL: `https://github.com/hritwij-shrivastava/Mern-Stack-Portfolio-Website.git`.
2. Remove the `./master` field and leave it blank.
3. Add a build step to execute a shell script:

```bash
# Copy project files
cp -R /home/ubuntu/jenkins/workspace/Mern-Stack-Portfolio-Website/backend /home/ubuntu/jenkins/workspace
cp /home/ubuntu/jenkins/workspace/.env /home/ubuntu/jenkins/workspace/backend

# Set permissions
cd /home/ubuntu/jenkins/workspace/
sudo chmod -R 777 backend

# Install Node.js dependencies and PM2
cd backend
npm i
npm install pm2@3.1.0 -g

# Configure Nginx
sudo nano /etc/nginx/sites-available/default
# Add the following lines in both the 80 and 443 location blocks:
# location / {
#     proxy_pass http://localhost:9000;
# }

sudo nginx -t
sudo systemctl restart nginx

# Set up PM2
pm2 startup
# Create an account on pm2.io and get the command from the website:
pm2 link kgbvv9b7uyfhcdb p3n8lewp5l0etci

# Monitor and start the Node.js application
pm2 monitor
pm2 start src/index.js
pm2 stop all
```

In the Jenkins backend config, add the following in the description:

```bash
pm2 stop all
```

---

## 8. Final React Code

Install the necessary dependencies for your React project:

```bash
npx create-react-app frontend .
npm install react-router-dom
npm i --save react-tsparticles@1.43.1
npm install react-bootstrap bootstrap
npm i moment
npm i react-google-recaptcha
npm i jwt-decode react-redux redux redux-thunk
npm i axios
npm i is-empty
npm install react-slick --save
npm i react-syntax-highlighter
npm install react-modal-video --force
npm i react-image-lightbox --force
npm install pdfjs-dist@2.13.216
npm install @react-pdf-viewer/core@3.3.2
npm install '@react-pdf-viewer/default-layout'
npm i canvas
```

To prevent source map generation in production, create a `.env` file with the following content:

```
GENERATE_SOURCEMAP=false
```

For a production build, install these additional dependencies:

```bash
npm i -D @babel/core @babel/preset-env @babel/preset-react babel-loader file-loader css-loader style-loader url-loader sass-loader sass webpack webpack-cli
npm i -D mini-css-extract-plugin
```

Create a `.babelrc` file with the following content:

```json
{
    "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

Create a webpack configuration file (check a sample webpack file in your directory).

---

## 9. Install Node.js on Ubuntu 18.04 LTS AWS

You can install Node.js on your Ubuntu 18.04 LTS AWS instance using one of the following methods:

### Using NodeSource:

```bash
cd /home/ubuntu/jenkins/workspace/backend