# Getting Started

Welcome to Qooxdoo! Qooxdoo is a one-stop javascript framework that helps you write single page web applications in pure JavaScript without touching HTML or CSS.

Qooxdoo applications are written in javascript. The qooxdoo framework is a large, well structured class library composed from both graphical and non graphical element you can use to build your applications. The following guide will show how this works in practice.

This guide takes less than 10 minutes to complete.

## Installation

Before you can load a qooxdoo application in your browser, it has to be compiled. The compilation step takes care including all the qooxdoo classes into your application that were referenced either directly or indirectly from your code.

The qooxdoo compiler is called `qx` and runs in nodes.js. Qooxdoo requires Node.js version 8.x or 10.x. to work.

To check your version, run `node -v` in a terminal/console window.

If you don't have node installed, or your version is too old, either go to [nodejs.org](https://nodejs.org) or use the [nvm system](https://github.com/nvm-sh/nvm) to get up and running.

Node comes with its own package manager called npm which you can now use to install the qooxdoo framework and the qooxdoo compiler. There are two ways to setup qooxdoo. You can install it in the same directory as your qooxdoo project or you can install it globally.

### Global installation

The following command line installs the qooxdoo compiler so that it becomes available via your path settings.

```console
$ npm install -g @qooxdoo/compiler @qooxdoo/framework
```

To start the qooxdoo compiler type

```console
$ qx
```

### Local Installation

Both the compiler and the qooxdoo framework are evolving, so if you are writing a large application which you may have to maintain for months and years to come, you will probably be better of to install qooxdoo together with the application code.

```console
$ mkdir myapp
$ cd myapp
$ npm install --save-dev @qooxdoo/compiler @qooxdoo/framework
```

To start the qooxdoo compiler type

```console
$ npx qx
```

Looking at the myapp directory you find two files: `package.json` and `package-lock.json` as well as a folder `node_modules`. Add the `package.json` and `package-lock.json` to your project files. This will allow you later to re-install the exact same version of the compiler and of the framework by typing `npm i` without the need to keep a copy of the `node_modules` folder around.
