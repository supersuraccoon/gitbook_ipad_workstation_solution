# Node.js && Express on Heroku 

## Foreword
This post is about how to set up a `HelloWorld` project using `Node.js` + `Express` on `Heroku`.

A offcial tutorial can be found [here](https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction).

## Workflow

### Install `heroku-toolbelt.pkg` 

```shell
root:heroku supersuraccoon$ ls
heroku-toolbelt.pkg
```

### Init `heroku`

```shell
root:heroku supersuraccoon$ heroku login
heroku-cli: Installing CLI... 21.02MB/21.02MB
Enter your Heroku credentials.
Email: supersuraccoon@gmail.com
Password (typing will be hidden): 
Logged in as supersuraccoon@gmail.com
```

### Check Environment

```shell
root:heroku supersuraccoon$ node -v
v4.4.3
root:heroku supersuraccoon$ npm -v
3.9.2
root:heroku supersuraccoon$ git --version
git version 2.4.9
```

### Init `node-js` `Git Project`

```shell

root:heroku supersuraccoon$ git clone https://github.com/heroku/node-js-getting-started.git
Cloning into 'node-js-getting-started'...
remote: Counting objects: 470, done.
remote: Total 470 (delta 0), reused 0 (delta 0), pack-reused 470
Receiving objects: 100% (470/470), 228.44 KiB | 34.00 KiB/s, done.
Resolving deltas: 100% (72/72), done.
Checking connectivity... done.
root:heroku supersuraccoon$ ls
node-js-getting-started
```
###Create `Heroku` App
```shell

root:node-js-getting-started supersuraccoon$ heroku create
Creating app... done, ⬢ stormy-sierra-97161
https://stormy-sierra-97161.herokuapp.com/ | https://git.heroku.com/stormy-sierra-97161.git
root:node-js-getting-started supersuraccoon$ ls -al
```
###Push `Git Project` to `Heroku` 

```shell
root:node-js-getting-started supersuraccoon$ git push heroku master
Counting objects: 453, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (351/351), done.
Writing objects: 100% (453/453), 225.90 KiB | 0 bytes/s, done.
Total 453 (delta 68), reused 452 (delta 68)
remote: Compressing source files... done.
remote: Building source:
remote: 
remote: -----> Node.js app detected
remote: 
remote: -----> Creating runtime environment
remote:        
remote:        NPM_CONFIG_LOGLEVEL=error
remote:        NPM_CONFIG_PRODUCTION=true
remote:        NODE_ENV=production
remote:        NODE_MODULES_CACHE=true
remote: 
remote: -----> Installing binaries
remote:        engines.node (package.json):  5.9.1
remote:        engines.npm (package.json):   unspecified (use default)
remote:        
remote:        Downloading and installing node 5.9.1...
remote:        Using default npm version: 3.7.3
remote: 
remote: -----> Restoring cache
remote:        Skipping cache restore (new runtime signature)
remote: 
remote: -----> Building dependencies
remote:        Pruning any extraneous modules
remote:        Installing node modules (package.json)
remote: 
remote: -----> Build succeeded!
remote:        ├── ejs@2.4.1
remote:        └── express@4.13.3
remote:        
remote: -----> Discovering process types
remote:        Procfile declares types -> web
remote: 
remote: -----> Compressing...
remote:        Done: 12.3M
remote: -----> Launching...
remote:        Released v3
remote:        https://stormy-sierra-97161.herokuapp.com/ deployed to Heroku
remote: 
remote: Verifying deploy.... done.
To https://git.heroku.com/stormy-sierra-97161.git
 * [new branch]      master -> master
```
### Run
```shell

root:node-js-getting-started supersuraccoon$ heroku ps:scale web=1
Scaling dynos... done, now running web at 1:Free
root:node-js-getting-started supersuraccoon$ heroku open
```
This will open a brwoser and you can see the template node.js project is running :

 ![heroku_nodejs_template](snapshot/heroku_nodejs_template.png)

### Hello World

Modfy the template project:

```
+ node-js-getting-started
	- app.json
	- index.js
	- package.json
	- Procfile
```

```javascript
var express = require('express');
var app = express();

app.set('port', (process.env.PORT || 5000));
app.get('/', function (req, res) {
	console.log('Request received');
  	res.send('Hello World');
});
app.listen(app.get('port'), function() {
  	console.log('Node app is running on port', app.get('port'));
});
```

And the deploy it to `heroku` again and here is the result:

 ![heroku_nodejs_helloworld](snapshot/heroku_nodejs_helloworld.png)



## Working Copy

Here is how to clone the project in [Working Copy, Git on iOS](http://workingcopyapp.com/).

### Check the `Git URL` 


```shell

root:node-js-getting-started supersuraccoon$ git remote -v
heroku  https://git.heroku.com/stormy-sierra-97161.git (fetch)
heroku  https://git.heroku.com/stormy-sierra-97161.git (push)
origin  https://github.com/heroku/node-js-getting-started.git (fetch)
origin  https://github.com/heroku/node-js-getting-started.git (push)
```

### Check Account Infomation

```shell
root$ vi ~/.netrc
machine api.heroku.com
  login supersuraccoon@gmail.com
  password xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
machine git.heroku.com
  login supersuraccoon@gmail.com
  password xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

### Clone in `Working Copy`

Input the `account` and `git url` in the `Remote URL`.

![working_copy_clone_heroku_1](snapshot/working_copy_clone_heroku_1.png)

![working_copy_clone_heroku_2](snapshot/working_copy_clone_heroku_2.png)

If you do not want to be ask for password everytime you fetch / push, you can add the password in the remote url like :

```
https://account_name:password@git_url
```
And then the remote project will be cloned successfully.

![working_copy_clone_heroku_2](snapshot/working_copy_clone_heroku_3.png)



