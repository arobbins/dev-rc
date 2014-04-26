A personal Frontend Taxonomy
=================================
> This repository documents my journey of becoming an expert at my craft. I plan to document everything that I've found to be confusing, helpful, and interesting. Hopefully you'll find it useful too =)

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

#### `.DS_Store`
The .DS_Store (Desktop Services Store) file keeps custom attributes of a folder such as the position of icons or the choice of a background image.

## Unix Commands
#### `wget`
GNU Wget is a free utility for non-interactive download of files from the Web. It supports HTTP, HTTPS, and FTP protocols, as well as retrieval through HTTP proxies. (Note: add -c flag to resume a broken download).

## Definitions
#### Bash
Bash (Bourne Again SHell) is the default shell on OSX and Linux.

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
#### Markdown formatting
[Markdown Basics](http://markdown-guide.readthedocs.org/en/latest/basics.html)
[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#lines)
Single line breaks are created by ending a line with two or more spaces


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

#### Mass find and move of files within unix
`sudo find /Volumes/Expansion\ Drive/Reason\ Refills -iname "*rhode*" -type f -exec /bin/mv {} /dump/rhodes \;`

#### Selecting only a certain amount of records in a SQL query
`select top 10 * from`

#### Flip Between Windows in Current Application
```Command + ` ```

## CSS Reminders
#### Reseting the box model using box-sizing reset
``` css
/* apply a natural box layout model to all elements */
*, *:before, *:after {
  -moz-box-sizing: border-box; -webkit-box-sizing: border-box; box-sizing: border-box;
 }
```
http://www.paulirish.com/2012/box-sizing-border-box-ftw

#### WTF, HTML and CSS?
http://wtfhtmlcss.com

## NPM
`--save-dev` updates package.json

## HTTP Status Codes
Code  | Status
----- | -------------
200	| Ok
404	| Forbidden
404	| Not found
500	| Internal Server Error

http://httpstat.us

## Inspiring links
- http://ejohn.org/blog/write-code-every-day (Writing code everyday)
- http://toddmotto.com/mastering-the-module-pattern (JS Module pattern)
- http://www.bobholt.me/2012/08/using-the-revealing-module-pattern (JS Module pattern)
- http://carldanley.com/js-revealing-module-pattern (JS Module pattern)
- https://www.interviewcake.com/tips-and-tricks (Interview techniques)