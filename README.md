A Personal Frontend Taxonomy
============================
This repository documents my journey of becoming an expert at my craft. Everything from definitions, file descriptions, language concepts, and 3rd party resources are listed here. I document everything that I've found to be confusing, helpful, and interesting to further my knowledge of web development. Hopefully you'll find it useful too =)

## File Descriptions
| Name | Description |
| --------------- | ----------- |
| `.bashrc` & `.bash_profile` | On OS X, when you open a new terminal window it logs the user into a new bash shell. Upon login, bash will first read the file `/etc/profile` for root level commands. Then bash will go to your home directory `~/` and read the following four files in the order in which they're found: `~/.bash_profile`, `~/.bash_login`, `~/.profile`, `~/.login`. For example, if you don't have a `.bash_profile` in your home directory, bash will then try to find `.bash_login`, and then `.profile`, etc. After opening a new terminal window, any additional windows are opened in a new bash *subshell*. Bash will then attempt to find `~/.bashrc` for the commands it needs. Additionally, after logging out of a Bash shell `~/.bash_logout` is run. To handle the discrepency between the login shell and the non-login shell, put the following in `~/.bash_profile`:
```
if [ -f ~/.bashrc ]; then
	source ~/.bashrc
fi
```

## Unix Commands
| Name | Description |
| --------------- | ----------- |
| `wget`			| GNU Wget is a free utility for non-interactive download of files from the Web. It supports HTTP, HTTPS, and FTP protocols, as well as retrieval through HTTP proxies.

## Definitions
| Name | Definition |
| --------------- | ----------- |
| Bash			| Bash (Bourne Again SHell) is the default shell on OSX and Linux.

## How tos
### Markdown formatting
[Markdown Basics](http://markdown-guide.readthedocs.org/en/latest/basics.html)  
[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#lines)  
Single line breaks are created by ending a line with two or more spaces

### Adding SSH access to your Github account
This assumes you have an SSH key generated already on your local machine. If not, follow [this tutorial](http://git-scm.com/book/en/Git-on-the-Server-Generating-Your-SSH-Public-Key). Also assumes you're on a *nix based OS.

* `cd ~/.ssh`  
* `pbcopy < ~/.ssh/id_rsa.pub`  
* Now paste it to your Github account  