# Intro to Grunt
====================================
#### Tutorial Links:
http://24ways.org/2013/grunt-is-not-weird-and-hard/
https://github.com/gruntjs/grunt-contrib-jshint

Grunt is a task runner, it can concatenate css and javascript, compress css and minify JavaScript, Optimize images. Grunt brings everything under one roof.

Grunt runs on Node.js

Grunt is a command line tool
To run grunt navigate to the project's directory, type grunt and press Return.

## Installation
---------------------------------------
- Install Node
* Grunt is install on a per-project basis. In the project folder create a package.json at the root level.

The contents should look like so:
```
{
  "name": "example-project",
  "version": "0.1.0",
  "devDependencies": {
    "grunt": "~0.4.1"
  }
}
```
* This is how Node does dependencies.
- npm install
* there should now be a node_modules folder
* Install the Grunt CLI
- npm install -g grunt-cli
- close and reopen the terminal

## Concatenation with Grunt
---------------------------------------
Ex. project
Three js files
* In production these files would be concatenated together for performance reasons.

##### grunt-contrib-concat
- npm install grunt-contrib-concat --save-dev
* This updated package.json to include this new dependency.

### Configure Grunt
- create file Gruntfile.js

##### Format
```
module.exports = function(grunt) {

    // 1. All configuration goes here
    grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),

        concat: {
            // 2. Configuration for concatinating files goes here.
        }

    });

    // 3. Where we tell Grunt we plan to use this plug-in.
    grunt.loadNpmTasks('grunt-contrib-concat');

    // 4. Where we tell Grunt what to do when we type "grunt" into the terminal.
    grunt.registerTask('default', ['concat']);

};
```

- list file paths under src in an array of file paths.
```
concat: {
    dist: {
        src: [
            'js/libs/*.js', // All JS in the libs folder
            'js/global.js'  // This specific file
        ],
        dest: 'js/build/production.js',
    }
}
```
* dest is the destination file and doesn't need to exist yet. It'll be created after running the task.

- place library files in their own /js/libs/ folder.
- global.js with our code goes in /js/ folder.
- after the task everything will be squished in production.js. The name indicates it will be used on our real live website.

- run grunt
- production.js is created
