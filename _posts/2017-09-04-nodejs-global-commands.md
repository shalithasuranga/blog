---
layout: post
title:  "Making global commands with NodeJS"
author: "Shalitha Suranga"
---

I guess you are creating new files using `touch` command. `touch` command works anywhere inside your OS. it means it's a global command. Here I am going to explain how you can register your own global command with NodeJS. 

I am going to develop very simple command `newhtml` that will create new html file with the HTML5 template.

Very first create a new folder `newhtml` 


> $ mkdir newhtml
> 
> $ cd newhtml

Create package.json

> $ npm init

Now I am going to modify the package.json to add my global command

    {
      "name": "newhtml",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "",
      "license": "ISC",
      "bin": {
    	"html5": "./bin/newhtml.js"
      }
    }


Now I mentioned that If I enter `newhtml` command anywhere I need to run the `bin/newhtml.js` script.

Create `bin` folder and touch `newhtml.js`

> $ mkdir bin
> 
> $ cd bin
> 
> $ touch newhtml.js

Thereafter we need to store the template in html file. Therefore create go back to project folder and create `template.html` with following content

    <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset="UTF-8">
    		<title>Title of the document</title>
    	</head>
    
    	<body>
    		Content of the document......
    	</body>
    
    </html>

Now develop the `newhtml.js` file

    #!/usr/bin/env node
    
    'use strict';
    
    var fs = require('fs'); 
    
    var filename = process.argv[2];
    
    if(typeof filename == 'undefined'){
    	filename = 'index.html';
    }
    else{
    	filename = filename + '.html';
    }
    
    fs.readFile(__dirname+'/../template.html','utf8', function(err,data){
    	fs.writeFile(process.cwd()+'/'+filename,data,'utf8',function(err, data){
    		console.log(filename+' created.');
    	});
    });


Bingo! you did coding. Now We will install this as a global module. Change the directory to your project root and run npm.

> $ npm install -g

Go to desktop and enter following commands

> $ newhtml myhtmlPage
>  
> $ newhtml 

Remove your global command using

> $ npm install -g


Happy coding !
















