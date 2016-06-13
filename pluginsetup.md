#evo-plugin-ios

## Steps to install and set up EVO SNAP SDK Cordova plugin for iOS

###Download PlugIn Source code

Download source code from this link and unzip somewhere you maintain source code of your projects.

[Source code](https://drive.google.com/open?id=0B7Pg8CqDFMwLSkRkNTE5Ujd4TTQ)

## Set Up and Install Plugin for Cordova based app.

#####Install Cordova
If Cordova is not install, then install the cordova module using npm utility of Node.js. The cordova module will automatically be downloaded by the npm utility.

```bash
sudo npm install -g cordova
```

#####Cordova based project
Go to the directory where you maintain your source code, and create a cordova project:

```bash
cordova create hello com.example.hello HelloWorld
```

#####Add Platforms
All subsequent commands need to be run within the project's directory, or any subdirectories:

```bash
$ cd hello
```

Add the platforms that you want to target your app. We will add the 'ios' platform and ensure they get saved to config.xml:

```bash
$ cordova platform add ios --save
```

#####To check your current set of platforms:

```bash
$ cordova platform ls
```


#####Add Plugin

Install plugin by replacing <path-to-plugin-src-folder> to path of downloaded unzip source code.

```bash
cordova plugin add <path-to-plugin-src-folder>
```

Example path may be like as below 

```bash
cordova plugin add ./../../source-evo-plugin-dev/
```


#####See list of installed plugin
Use plugin ls (or plugin list) to view currently installed plugins. Each displays by its identifier, this should display installed plugin.

```bash
$ cordova plugin ls
```

## Set Up and Install Plugin for Ionic app

##Alternate flow to setup and install plugin on Ionic app, incase if you have installed ionic.

###Create ionic application 

```bash
ionic start myApp sidemenu
```

### Add platform iOS
```bash
ionic platform add ios
```

### Install plugin 
```bash
ionic plugin add ./../../source-evo-plugin-dev/
```

### See list of plugins
```bash
ionic plugin list
```

### Delete existing plugin
```bash
ionic plugin remove source-evo-plugin-dev
```

