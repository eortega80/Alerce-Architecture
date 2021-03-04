# ALERTRAN COMET DOC [![Build Status](https://travis.ibm.com/massimo-caprinali/alerce-alertran-docs.svg?token=1NhQL5guS3gQgLoXNKvF&branch=master)](https://travis.ibm.com/massimo-caprinali/alerce-alertran-docs) ![PyPI](https://img.shields.io/pypi/v/mkdocs?label=mkdocs) ![Docs Status](deploy-status.svg) ![Last Deploy](last-deploy.svg)
This is a repository to store documentation of the project.

## Install the tools

### Clone repository

``` sh
$ git clone https://github.ibm.com/massimo-caprinali/alerce-alertran-docs.git
```

### Use VSCode Dev Containers

VScode should propose using a dev container when you open the repo you just cloned. Otherwise open the Command Palette with `F1` and choose `Remote-containers: Build and open in Container`.

The dev container will install all the required tools to build this project and your dev environment will be inside a container.

### The hard way

In case you don't want to use a dev container, you can also install the tools directly on your computer.

#### Install required tools

Install Homebrew, if not done yet:

``` sh
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

Install Python 3.5, 3.6, 3.7 or 3.8:

``` sh
$ brew install python3
```

If you need to install pip for the first time or you installed python without Homebrew, download [get-pip.py](https://bootstrap.pypa.io/get-pip.py). Then run the following command to install it:

``` sh
$ python3 get-pip.py
```

Install all required dependencies:

``` sh
$ brew install cairo pango gdk-pixbuf libffi
```

``` sh
$ pip3 install -r requirements.txt
$ pip3 install git+https://github.com/rogerxaic/mkpdfs-mkdocs-plugin.git#egg=mkpdfs-mkdocs
```

### Compile the PDF theme

To compile the PDF theme, run the following.

``` sh
cd design
npm i 
npm run build
```

You might need to remove `node_modules` and re-run `npm i && npm run build` if you encounter any problems.

## Run on local environment

``` sh
mkdocs serve
```

## Deploy to GH Pages

``` sh
mkdocs build && mkdocs gh-deploy --remote-branch gh-pages
```

## Aliases

package.json

``` json
{
  "scripts": {
    "build": "mkdocs build",
    "start": "mkdocs serve",
    "build-css": "cd design && node-sass report.scss report.css",
    "build-css-compressed": "cd design && node-sass report.scss report.css --output-style compressed",
    "deploy": "mkdocs gh-deploy --force --remote-branch gh-pages"
  }
}
```

``` sh
$ npm run [build|start|build-css|build-css-compressed|deploy] 
```