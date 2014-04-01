An Autodidact's Frontend Taxonomy
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
GNU Wget is a free utility for non-interactive download of files from the Web. It supports HTTP, HTTPS, and FTP protocols, as well as retrieval through HTTP proxies.

## Definitions
#### Bash
Bash (Bourne Again SHell) is the default shell on OSX and Linux.

#### Asynchronous
A client (browser) can request new pieces of information from a server at anytime without needing a page reload. This request can be event driven (clicking on a button or hovering over an image for example).

#### XMLHttpRequest
XMLHttpRequest (XHR) is a JavaScript object that is used heavily in AJAX programming. XHR can retireve more than just XML&mdash;for example, JSON, file, and ftp. https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest

#### AJAX
AJAX stands for Asynchronous JavaScript and XML


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