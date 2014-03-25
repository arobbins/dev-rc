A Personal Frontend Taxonomy
============================
This repository documents my journey of becoming an expert at my craft. Everything from definitions, file descriptions, language concepts, and 3rd party resources are listed here. I document everything that I've found to be confusing, helpful, and interesting to further my knowledge of web development. Hopefully you'll find it useful too =)

## File Descriptions  
| Name | Description 								|
| --------------- | ----------- |
| `.bashrc`			| When an interactive shell that is not a login shell is started, bash reads and executes commands from ~/.bashrc

## Unix Commands  
| Name | Description 								|
| --------------- | ----------- |
| `wget`			| GNU Wget is a free utility for non-interactive download of files from the Web. It supports HTTP, HTTPS, and FTP protocols, as well as retrieval through HTTP proxies.

## How tos  
#### Markdown formatting
[Markdown Basics](http://markdown-guide.readthedocs.org/en/latest/basics.html)  
[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#lines)  
Single line breaks are created by ending a line with two or more spaces

#### Adding SSH access to your Github account
This assumes you have an SSH key generated already on your local machine. If not, follow [this tutorial](http://git-scm.com/book/en/Git-on-the-Server-Generating-Your-SSH-Public-Key). Also assumes you're on a *nix based OS.

1. `cd ~/.ssh`  
2. `pbcopy < ~/.ssh/id_rsa.pub`  
3. Now paste it to your Github account  