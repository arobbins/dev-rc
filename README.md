Notes
=====================
> References, reminders, resources

## Bugs

### Issue: WordPress shows Error establishing Database connection
Solution: Make sure you have the correct .htaccess file and that the file permissions are correct

### Issue: WordPress Media Library displays 404 error / admin-ajax.php not found
Solution: Permissions are incorrect on the wp-content folder. Temporarily changing to 777 fixed the issue.

### Issue: Sublime Text 3 triggers high CPU usage
Solution: Add the following to user config:"index_files": false

### Issue: WordPress 500 Internal error
Solution: Fix permissions, and add .htaccess

### Issue: Migrabte DB Pro failing on media transfer
Solution: As far as I can tell this only occurs when attempting a tranfer from localhost to remote. Pulling from another remote fixed it for me.

### Issue: A Small Orange caching persisting on CSS
Solution: ASO has a hard 15min server cache for their shared-hosting plans. Use ?nocache=1 to bypass

### Issue: A Small Orange 500 Internal Service Error
Solution: This has always been a permissions error for me. Make sure the correct permissions are present. See "Correct permissions"

### Issue: Angular dependencies not loading
Solution: Make sure they're in the correct order

## Issue: WP Migrate DB Connection error
Solution: Try unchecking SSL verification on local site

## Issue: A Small Orange can't login to wordpress backend
Solution: Make sure PHP is 5.5 +. The bcrypt plugin inside mu-plugins needs it


## File Descriptions
#### `.bashrc` & `.bash_profile`
On OS X, when you open a new terminal window it logs the user into a new bash shell. Upon login, bash will first read the file `/etc/profile` for root level commands. Then bash will go to your home directory `~/` and read the following four files in the order in which they're found: `~/.bash_profile`, `~/.bash_login`, `~/.profile`, `~/.login`. For example, if you don't have a `.bash_profile` in your home directory, bash will then try to find `.bash_login`, and then `.profile`, etc.

After opening a new terminal window, any additional windows are opened in a new bash *subshell*. Bash will then attempt to find `~/.bashrc` for the commands it needs. Additionally, after logging out of a Bash shell `~/.bash_logout` is run.

To handle the discrepency between the login shell and the non-login shell, put the following in `~/.bash_profile`
```
if [ -f ~/.bashrc ]; then
	source ~/.bashrc
fi
```

#### Favicon
An .ico file is a container for multiple .bmp or .png icons of different sizes. Create your .ico out of optimized .png files.

#### `.DS_Store`
The .DS_Store (Desktop Services Store) file keeps custom attributes of a folder such as the position of icons or the choice of a background image.

## ethOS commands
#### Detailed view of what the cards are set at
`amdconfig --od-getclocks --adapter=all`

## Unix Commands
#### Rsync (sync) remote dir to local
rsync -anvzP --progress --rsh=ssh ostromcr@67.20.89.138:~/mail/ ./mail

#### sudo killall Finder
Restart the Finder

#### `wget`
GNU Wget is a free utility for non-interactive download of files from the Web. It supports HTTP, HTTPS, and FTP protocols, as well as retrieval through HTTP proxies. (Note: add -c flag to resume a broken download).

#### 'cat ~/.ssh/id_rsa.pub | ssh user@server 'cat >> .ssh/authorized_keys''
Copies your public key to the authorized_keys file on remote server

#### 'chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys'
Changes correct permissions of .ssh folder and authorized_keys file

#### 'zip -r --password (password) (filename) (folder)'
Recursively zip a directory and password protect it

#### 'find ./ -type f -name '*.jpg' -exec du -ch {} + | grep total$'
Show total file size of a given dir

#### tar -zcvf archive_name.tar.gz folder_to_compress
.tar compression

#### tar -zxvf archive_name.tar.gz
.tar extraction

#### sudo rm -rf ~/.Trash/*
Force empty trash

#### Change user password
'passwd' and follow the promopt

## Definitions
#### Bash
Bash (Bourne Again SHell) is the default shell on OSX and Linux.

#### Semantic difference between Parameters and Arguments
**Parameters:** A property you set on a function when initially defining it

**Arguments:** The value you pass into a function when calling it

#### Asynchronous
A client (browser) can request new pieces of information from a server at anytime without needing a page reload. This request can be event driven (clicking on a button or hovering over an image for example). Not occurring at the same time.

#### XMLHttpRequest
XMLHttpRequest (XHR) is a JavaScript object that is used in AJAX programming. XHR can retrieve more than just XML. For example, JSON, file, and ftp. https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest. The XHR object contains methods that are used to make HTTP requests. The common methods are:

readyState (the state of the request)
0	UNSENT	open()has not been called yet.
1	OPENED	send()has not been called yet.
2	HEADERS_RECEIVED	send() has been called, and headers and status are available.
3	LOADING	Downloading; responseText holds partial data.
4	DONE	The operation is complete.

onreadystatechange
A JavaScript function object that is called whenever the readyState attribute changes. The callback is called from the user interface thread.

responseText
The response to the request as text, or null if the request was unsuccessful or has not yet been sent.

Object properties  | Definition
:----------------- | :-------------
onreadystatechange | A JavaScript function object that is called whenever the readyState attribute changes. The callback is called from the user interface thread.
readyState			 | Indicates the state of the request. The value is a number between 0-4. 0 = UNSENT, 1 = OPENED, 2 = HEADERS_RECEIVED, 3 = LOADING, 4 = DONE.
responseText		 | The response to the request as text, or null if the request was unsuccessful or has not yet been sent.
status 				 | The status of the response to the request. This is the HTTP result code (for example, status is 200 for a successful request).

#### AJAX
Asynchronous JavaScript and XML

#### ulimit
ulimit is a *nix preference that limits system resources started by the shell itself. The `-n` flag describes how many file descriptors can be opened at once.
> "In simple words, when you open a file, the operating system creates an entry to represent that file and store the information about that opened file. So if there are 100 files opened in your OS then there will be 100 entries in OS (somewhere in kernel). These entries are represented by integers like (...100, 101, 102....). This entry number is the file descriptor. So it is just an integer number that uniquely represents an opened file in operating system. If your process open 10 files then your Process table will have 10 entries for file descriptors. Similarly when you open a network socket, it is also represented by an integer and it is called Socket Descriptor."

http://stackoverflow.com/questions/5256599/what-are-file-descriptors-explained-in-simple-terms
http://ss64.com/bash/ulimit.html


## How tos
#### Reset WordPress password via MySQL
UPDATE `wp_users` SET `user_pass`= MD5('yourpass') WHERE `user_login`='arobbins';

#### Markdown formatting
[Markdown Basics](http://markdown-guide.readthedocs.org/en/latest/basics.html)
[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#lines)
Single line breaks are created by ending a line with two or more spaces

#### Installing Grunt
In order to get started with Grunt, you first need to install the command within your system directory. To do this, install the grunt command-line interface below:

`npm install -g grunt-cli`

Once this the Grunt CLI is installed, make sure you have a companion package.json file in your project and you should be good to go.

[Resource 1] (http://gruntjs.com/getting-started)
[Resource 2] (https://frontendmasters.com/courses/workflows-and-tooling)

#### Adding SSH access to your Github account
This assumes you have an SSH key generated already on your local machine. If not, follow [this tutorial](http://git-scm.com/book/en/Git-on-the-Server-Generating-Your-SSH-Public-Key). Also assumes you're on a *nix based OS.

* `cd ~/.ssh`
* `pbcopy < ~/.ssh/id_rsa.pub`
* Now paste it to your Github account


#### Associating Text Editors with Git
`git config --global core.editor "subl -n -w"`
https://help.github.com/articles/associating-text-editors-with-git

#### Less verbose git status message
`git status -sb`

#### Stage all tracked files in Git
`git add -u`

#### Show changed files in specific commit
'git show --pretty="format:" --name-only bd61ad98'

#### Mass find and move of files within unix
`sudo find /Volumes/Expansion\ Drive/Reason\ Refills -iname "*rhode*" -type f -exec /bin/mv {} /dump/rhodes \;`

#### Selecting only a certain amount of records in a SQL query
`select top 10 * from`

#### Flip Between Windows in Current Application
```Command + ` ```

#### Vertically center anything
``` css
.parent-element {
  -webkit-transform-style: preserve-3d;
}
.element {
  position: relative;
  top: 50%;
  transform: translateY(-50%);
}
```

#### Horizontally center absolutely positioned element
``` css
.parent-element {
  position: relative;
}
.element {
	width: 25%;
	position: absolute;
	left: 0;
	right: 0;
	text-align: center;
}
```

#### Building and Installing Lua on Mac
- http://www.lua.org/faq.html#1.1

```
curl -R -O http://www.lua.org/ftp/lua-5.2.3.tar.gz
tar zxf lua-5.2.3.tar.gz
cd lua-5.2.3
make macosx test
```

#### How Arrays are objects behind the scenes
```js
var arr = [];
arr.push(10, 20);
arr["prop1"] = "value1";

// Behind the scenes
arr = {
	0: 10,
	1: 20,
	prop1: "value1"
}
```

#### Lexical Scoping
Predominate scoping model in JavaScript. Lexical scope also means "compile-time scope" (the time you wrote your code). Think of it like walking up the stairs of the building. The rooftop being the global scope. Another way of thinking of it is in terms of "bubbles". Each function contains a bubble that wraps nested functions. (https://frontendmasters.com/courses/advanced-javascript)

#### Dynamic Scoping
Dynamic scoping is created by using the this keyword as it binds object to specific things.

### This keyword
Every function, while executing, has a reference to its current executing context called "this".

Four rules for how the this keyword gets bound:
	1. Default - If you're in strict mode, default this to the undefined value. If you're not in strict mode, default this to the global object. Either undefined to global.
	2. Implicit binding - Contains a owning object
	3.
	4.

How to determine where 'this' is bound. Find the callsite, ask these four rules:
--------------------------------------------------------------------------------
1. Was the function called with the new keyword?
2. Was the function called with call or apply specifying an implicit 'this'?
3. Was the function called via a containing object (context)?
4. Default: global object

### New keyword
When you place the new keyword infront of any function call, it turns it into a constructor call that does 4 things.
1. A brand new empty object will be created
2. That object gets linked to a different object*
3. That object gets bound to the this keyword
4. If that object does not otherwise return anything it will implicitly insert a return "this".

### Speed Test program
```js
// Primitives Array - 150 items
var listPrim = [12.42423, 324.42423, 4.42423, 25.42423, 65.42423, 23.42423, 532.42423, 24.42423, 535.42423, 747.42423, 5.42423, 4365.42423, 63.42423, 35.42423, 62.42423, 46.42423, 52.42423, 225.42423, 6436.42423, 23.42423, 53.42423, 52.42423, 5.42423, 26.42423, 35.2, 12.42423, 324.42423, 4.42423, 25.42423, 65.42423, 23.42423, 532.42423, 24.42423, 535.42423, 747.42423, 5.42423, 4365.42423, 63.42423, 35.42423, 62.42423, 46.42423, 52.42423, 225.42423, 6436.42423, 23.42423, 53.42423, 52.42423, 5.42423, 26.42423, 35.2, 12.42423, 324.42423, 4.42423, 25.42423, 65.42423, 23.42423, 532.42423, 24.42423, 535.42423, 747.42423, 5.42423, 4365.42423, 63.42423, 35.42423, 62.42423, 46.42423, 52.42423, 225.42423, 6436.42423, 23.42423, 53.42423, 52.42423, 5.42423, 26.42423, 35.2, 12.42423, 324.42423, 4.42423, 25.42423, 65.42423, 23.42423, 532.42423, 24.42423, 535.42423, 747.42423, 5.42423, 4365.42423, 63.42423, 35.42423, 62.42423, 46.42423, 52.42423, 225.42423, 6436.42423, 23.42423, 53.42423, 52.42423, 5.42423, 26.42423, 35.2, 12.42423, 324.42423, 4.42423, 25.42423, 65.42423, 23.42423, 532.42423, 24.42423, 535.42423, 747.42423, 5.42423, 4365.42423, 63.42423, 35.42423, 62.42423, 46.42423, 52.42423, 225.42423, 6436.42423, 23.42423, 53.42423, 52.42423, 5.42423, 26.42423, 35.2, 12.42423, 324.42423, 4.42423, 25.42423, 65.42423, 23.42423, 532.42423, 24.42423, 535.42423, 747.42423, 5.42423, 4365.42423, 63.42423, 35.42423, 62.42423, 46.42423, 52.42423, 225.42423, 6436.42423, 23.42423, 53.42423, 52.42423, 5.42423, 26.42423, 35.2];

var SpeedTest = function(func, params, reps){
	this.func = func;
	this.params = params;
	this.reps = reps || 10000;
	this.average = 0;
};

SpeedTest.prototype = {
	startTest: function(){

		// Set up variables
		var beginTime,
			 endTime,
			 sumTimes = 0;

		// Check for valid params
		if(this.func(this.params) === false ){
			alert("Yo man, the test failed with those parameters.");
			return;
		}

		// Start the test
		for (var i = 0, x = this.reps; i < x; i++){
			beginTime = +new Date();
			this.func(this.params);
			endTime = +new Date();
			sumTimes += endTime - beginTime;
		}

		// Find the average
		this.average = sumTimes / this.reps;

		// Return result!
		return console.log("Average execution across " + this.reps + " repetitions: " + this.average);
	}
};

var logger = function(element, index, array) {
	console.log(element.toFixed());
};

var looper = function(func){
	listPrim.forEach(func);
}

var myTest = new SpeedTest(looper, logger, 5000);
```

#### Classes, Prototypes, and Inheritance In Javascript
Classes don't natively exist in Javascript. However you can implement a Class-like architecture through the use of Constructor functions:

```js
function Person(name, age, location){
	this.name = name;
	this.age = age;
	this.location = location;
	this.motto = "Tu ne cede malis";
	this.sayMotto = function(){
		return alert(this.motto);
	};
};
var andy = new Person("Andy", 26, "Minneapolis");
andy.sayMotto();
```

All objects in Javascript have a prototype object. The prototype object is a semi-hidden property sometimes seen in browsers as `__proto__`.

We can be more efficient in our code if we abstract our sayMotto function into the Person prototype instead. For example:

```
function Person(name, age, location){
	this.name = name;
	this.age = age;
	this.location = location;
	this.motto = "Tu ne cede malis";
};
Person.prototype.sayMotto = function(){
	return alert(this.motto);
};
var andy = new Person("Andy", 26, "Minneapolis");
andy.sayMotto(); // Works the same way

```
Additionally, the `instanceof` operator can tell you what Prototype / Constructor function your new object comes from.

#### Closures
Closure is when a function "remembers" its lexical scope even when the function is executed outside that lexical scope.

``` js

function foo() {
	var bar = "bar";
	function baz() {
		console.log(bar);
	}
	bam(baz);
}
function bam(baz) {
	baz();
}

foo();

```

#### Revealing Modular Pattern

``` js

var foo = (function(){

	var o = {
		bar: "bar"
	};

	return {
		bar: function(){
			console.log(o.bar);
		}
	}

})();

foo.bar();

```

#### Configuring the subl command
- http://stackoverflow.com/questions/17733367/getting-sublimetext-to-run-from-terminal-in-mac

Make sure to put the binary in /usr/local/bin. The binary can be found in /Applications/Sublime\ Text.app/Contents/SharedSupport/bin

#### Copying SSH public key to clipboard

` pbcopy < ~/.ssh/id_rsa.pub `

#### Hiding mini-map by default in Sublime
- http://stackoverflow.com/questions/13877319/sublime-text-2-hide-minimap-by-default

` "show_minimap": false `

#### Adding custom keyboard shortcut to maximize current window on OSX
- 1) System Preferences - Keyboard
- 2) Shortcuts - App Shortcuts
- 3) Add new
- 4) Type in "Zoom" for Menu Title

#### Setting R+W permissions on a folder recursively
`chmod -R 777 <folder> `

#### Showing hidden files and folders on 10.9.3
`defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder`

#### List all Branches associated with a given respository
`git branch -a`

## Apache

#### Restore configuration after Mac OS updates
```
sudo cp /etc/apache2/httpd.conf~previous /etc/apache2/httpd.confcopy
sudo cp /etc/apache2/extra/httpd-vhosts.conf~previous /etc/apache2/extra/httpd-vhosts.conf
sudo apachectl restart
```

#### Test the current configuration of Apache

The below two commands do the same thing. More resources here: http://httpd.apache.org/docs/2.2/programs/apachectl.html

``` bash
apachectl configtest
```

``` bash
apachectl -t
```

## GIT
#### Show changed files from last commit
``` bash
git diff-tree --no-commit-id --name-only -r 952364b
```

#### Force Merge
``` bash
git fetch --all
git reset --hard origin/master
```

## CSS Reminders

#### List of Flexbox vendor prefixes
http://ptb2.me/flexbox

#### Prevent copy from wrapping underneath floated elements
http://stackoverflow.com/questions/11411219/css-to-stop-text-wrapping-under-image/15421257#15421257
``` css
/* Element not to be wrapped must be block-level */
img {
	float: left;
}
p {
	overflow: hidden
}
```

#### Clickable background-images
``` css
/* Instead of padding, use text-indent to move copy if needed */

.link {
	text-indent: 10%;
}
```

#### Reseting the box model using box-sizing reset
``` css
/* apply a natural box layout model to all elements */
*, *:before, *:after {
  -moz-box-sizing: border-box; -webkit-box-sizing: border-box; box-sizing: border-box;
 }
```
http://www.paulirish.com/2012/box-sizing-border-box-ftw

#### Set any container to 100% of viewport height
This is super useful if you want to set a full background-image to a container other than the body.
``` css
height: 100vh;
```
http://stanislav.it/how-to-make-div-element-100-height-of-browser-window-using-css-only

#### Horizontalling align floated element
``` css
margin: 0 10%;
```

#### Usefull SASS Mixins
``` scss
@function calculateRem($size) {
  $remSize: $size / 16px;
  @return $remSize * 1rem;
}

@mixin font-size($size) {
  font-size: $size;
  font-size: calculateRem($size);
}
```

## SSH
local dir: "~/.ssh"

## SCP
Upload file: "scp <file> <un>@<server>:~/"

## HTTP
- The default port for HTTP traffic is 80.

> To be able to fetch those quickly, browsers will make several requests simultaneously, rather than waiting for the responses one at a time.

> Making HTTP requests in web page scripts once again raises concerns about security. The person who controls the script might not have the same interests as the person on whose computer it is running. More specifically, if I visit themafia.org, I do not want its scripts to be able to make a request to mybank.com, using identifying information from my browser, with instructions to transfer all my money to some random mafia account. It is not too hard for websites to protect themselves against such attacks, but it requires effort, and many websites fail to do it. For this reason, browsers protect us by disallowing scripts to make HTTP requests to other domains (names like themafia.org and mybank.com).

## Gravity Forms
[gravityform id=1 title=false description=false ajax=true tabindex=49]

## Angular

### $scope
At its core, $scope is nothing more than a JavaScript object. For example,
``` js
$scope.name = "Andrew";
$scope.age = 26;
```
Renders as:
``` js
{
	name: "Andrew"
	age: 26
}
```
### $inject
The $inject property is a way in which you can inject your dependencies that minifiers will not break. It's similar to the array syntax when declaring your function parameters.

## PHP
php.ini file location: '/private/etc/php.ini'

## NPM
`--save-dev` updates package.json

## HTTP Status Codes
Code  | Status
----- | -------------
200	| Ok
403	| Forbidden
404	| Not found
500	| Internal Server Error

http://httpstat.us

## You Don't know JS Notes (Scope & Closures)
>  Note: LHS and RHS meaning "left/right-hand side of an assigment" doesn't necessarily literally mean "left/right side of the = assignment operator". There are several other ways that assignments happen, and so it's better to conceptually think about it as: "who's the target of the assignment (LHS)" and "who's the source of the assignment (RHS)".

> "Strict Mode", which was added in ES5, has a number of different behaviors from normal/relaxed/lazy mode. One such behavior is that it disallows the automatic/implicit global variable creation. In that case, there would be no global Scope'd variable to hand back from an LHS look-up, and Engine would throw a ReferenceError similarly to the RHS case.

## Wordpress

### Repo strategy
- Don't store Core files
  - These files shouldn't be changing in the first place

- Don't store sensitive information
  - Following security best practices

- Don't store uploads
  - Repo becomes out of date as soon as client uploads something new
  - Repo becomes way too large

- Store Theme
- Store Plugins

### Remove WYSIWYG editor on pages only

``` php

function remove_editor_on_pages() {
  global $_wp_post_type_features;

  $post_type = "page";
  $feature = "editor";

  if (!isset($_wp_post_type_features[$post_type])) {

  } else if (isset($_wp_post_type_features[$post_type][$feature])) {
    unset($_wp_post_type_features[$post_type][$feature]);
  }

}
add_action("init", "remove_editor_on_pages");

```

### Enable local installation of Plugins
Add below code to wp-config.php
``` php
define('FS_METHOD', 'direct');
```

#### Correct permissions

##### Directories
find . -type d -exec chmod 755 {} +

##### Files
find . -type f -exec chmod 644 {} +


### WooCommerce
#### API Docs http://docs.woothemes.com/wc-apidocs

## Redirects
#### Removing date within blog posts
``` bash
RedirectMatch 301 /blog/([0-9]+)/([0-9]+)/(.*)$ /blog/$3
```

## APIs
#### Consuming a WS through curl
curl -k -H "Accept:application/json" -H "Authorization: Basic YXJvYmJpbnNfcWE6QDhBfsdDdsskOKNaj4=" https://wsurlgoeshere.com

-k allows for an insecure connection
-H sets a header

## Databases
### MySQL
#### Importing mysql database
``` mysql
mysql -u username -p database_name < file.sql
```

#### Dumping mysql database
``` mysql
mysqldump -u username -p database_name > file.sql
```

#### Update database URLs
``` mysql
UPDATE wp_options SET option_value = replace(option_value, 'http://www.oldurl', 'http://www.newurl') WHERE option_name = 'home' OR option_name = 'siteurl';

UPDATE wp_posts SET guid = replace(guid, 'http://www.oldurl','http://www.newurl');

UPDATE wp_posts SET post_content = replace(post_content, 'http://www.oldurl', 'http://www.newurl');

UPDATE wp_postmeta SET meta_value = replace(meta_value,'http://www.oldurl','http://www.newurl');
```


## Shortcuts
### Chrome
- Opening Dev Console: CMD + Option + J
- Toggling console docking: CMD + Shift + D
- Enter mobile view: CMD + Shift + M

## Resources

### Inspiration
- http://ejohn.org/blog/write-code-every-day (Writing code everyday)
- http://toddmotto.com/mastering-the-module-pattern (JS Module pattern)
- http://www.bobholt.me/2012/08/using-the-revealing-module-pattern (JS Module pattern)
- http://carldanley.com/js-revealing-module-pattern (JS Module pattern)
- https://www.interviewcake.com/tips-and-tricks (Interview techniques)
- https://www.statwing.com/demos/dev-survey-2#workspaces/18726 (Stack Overflow 20,000 Survey)

### Git
- https://github.com/tj/git-extras (Git extras)

### Images
- https://varvy.com/pagespeed/base64-images.html (Base64 Encoding of images)

### JavaScript
- http://juliepagano.com/blog/2014/05/18/javascript-debugging-for-beginners (Debugging for beginners)
- https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch1.md (Scopes & Closure)
- http://promises-aplus.github.io/promises-spec (Promises 1)
- http://www.sitepoint.com/overview-javascript-promises (Promises 2)
- http://www.ecma-international.org/ecma-262/5.1 (Latest ECMA Spec)
- https://github.com/getify/You-Dont-Know-JS (Kyle Simpson - You don't know JS)
- https://github.com/rwaldron/idiomatic.js (Principles of Writing Consistent, Idiomatic JavaScript)
- https://www.youtube.com/watch?v=XP89VxObKO4 (Browser versions are dead - Kyle Simpson)
- http://toddmotto.com/mastering-the-module-pattern (Mastering the Module pattern)
- http://momentjs.com (Moment.js Dates in Javascript)
- http://youmightnotneedjquery.com (You might not need jquery)
- https://medium.com/javascript-scene/learn-javascript-b631a4af11f2 (Quality JS Learning resources)

### Angular
- https://www.udemy.com/angularjs-jumpstart/#/
- http://durated.github.io/angular-scroll (Angular Scroll)
- http://toddmotto.com/opinionated-angular-js-styleguide-for-teams (Angular Styleguide)
- http://ionicframework.com (Open-source front-end framework for building hybrid mobile apps)

### HTML
- http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom (Shadow DOM)
- http://ericportis.com/posts/2014/srcset-sizes/ (Srcset and sizes - responsive image technique)
- https://dev.opera.com/articles/native-responsive-images (Native responsive images)

### CSS
- http://alistapart.com/article/designing-for-breakpoints (Beyond breakpoints)
- http://wtfhtmlcss.com (Common CSS Gotchas)
- http://grumpicon.com (Tool for turning SVG's into CSS and producing .png fallbacks)
- http://drewbarontini.com/articles/single-responsibility/?utm_source=html5weekly&utm_medium=email (Modular CSS)
- http://csstriggers.com (Which CSS properties trigger repaints, reflows, etc)
- http://aerotwist.com/blog/css-triggers (Companion blog post to the above article)

### Wordpress
- http://polevaultweb.com/2014/03/5-ways-synchronise-wordpress-uploads-across-environments (Workflow tips)
- https://github.com/arobbins/wp-deploy-checklist (WP Deploy Checklist)

### HTTP / Server
- https://gist.github.com/jed/6147872 (Setting up local SSL)
- http://www.corsproxy.com (CORS Proxy)
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS (CORS)
- http://openmymind.net/2012/2/3/Node-Require-and-Exports (Node's require and exports)
- http://eloquentjavascript.net/17_http.html (HTTP chapter from Eloquent JavaScript second edition)

### Misc
- http://glaciertheme.com (Current Sublime theme)
- http://cdnjs.com (CDNs)
- https://github.com/josephyzhou/github-trending (Github trending, nice)
- http://frontendbabel.info/articles/webpage-rendering-101 (What ever Frontend Dev should know...)
- http://www.sitepoint.com/conduct-fair-meaningful-technical-interview (Interview questions)
- http://justinhileman.info/article/git-pretty/full (Git workflow chart -- very helpful)
- https://github.com/audreyr/favicon-cheat-sheet (Favicon best practices)
- http://realfavicongenerator.net (Favicon generator)
- http://exercism.io (Hands on learning tool for programming)
- http://developer.telerik.com/featured/scroll-event-change-ios-8-big-deal (New iOS scroll functionality)

### Optimization
- http://compressor.io (image compression)
- http://blog.arvidandersson.se/2014/06/17/best-practices-in-modern-web-projects (Best Practices in Modern Web Applications)
- http://scottjehl.github.io/picturefill/#download (Responsie Images)
- http://filamentgroup.com/lab/performance-rwd.html (Making responsive sites faster)

### Unix
- http://www.oliverelliott.org/article/computing/tut_unix/#Introduction (Intro to Unix)
