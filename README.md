# Command Line hands on

![Alt text](./linux.svg?raw=true,"View")

## Usage
<ul>
 <li>Clear history: <b>`ctrl + l`</b></li>

<li>Clear everything left from current cursor position: <b>`ctrl + u`</b></li>

<li>Clear everything right from current cursor position: <b>`ctrl + k`</b></li>

<li>Re-call last input with sudo: <b>`sudo !!`</b></li>

<li>Stop current process: <b>`ctrl + c`</b></li>

<li>Jump to left: <b>`ctrl + a`</b></li>

<li>Jump to right: <b>`ctrl + e`</b></li>

<li>Help: <b>`help cd` / `help dir`</b> (...)</li>

<li>Finding Help: <b>`apropos directory` / `apropos search`</b> (...)</li>

<li>Define custom startup screen: <b>`sudo nano /etc/motd`</b></li>

<li>Run a script as background process: <b>`python script.py &`</b></li>

<li>List all running process's: <b>`ps aux`</b></li>

<li>Kill a running process: <b>`sudo kill 12345`</b></li>
</ul>

## System
<ul>
<li>Get the current path: <b>`pwd`</b></li>

<li>Copy to clipboard: <b>`pwd | pbcopy`</b></li>

<li>Paste: <b>`pbpaste`</b></li>

<li>Get the current hostname: <b>`hostname`</b></li>

<li>Get the current users: <b>`users`</b></li>

<li>Get all info about the environment: <b>`env`</b></li>

<li>Show calendar: <b>`cal`</b></li>

<li>Show today's date: <b>`date`</b></li>

<li>Exit terminal: <b>`exit`</b></li>
</ul>

## Permissions

<ul>
 <li>Use <b>`-R`</b> option to change permissions recursively.</li>

<li>List: <b>`ps -ef | grep apache | grep -v grep`</b></li>

<li>Change permissions: <b>`chmod 755 index.php`</b></li>

<li>Change owner: <b>`chown root index.php` (`root` is the username)</b></li>

<li>Change group: <b>`chgrp www-data index.php` (`www-data` is the groupname)</b></li>
</ul>

### WordPress Files/Folder Permissions
Let apache be owner: `chown www-data:www-data -R *`

Change directory permissions rwxr-xr-x: `find . -type d -exec chmod 755 {} \;`

Change file permissions rw-r--r--: `find . -type f -exec chmod 644 {} \;`

(see http://stackoverflow.com/a/18352747/1815847)

## Directories
List directory contents: `ls`

List all directory contents: `ll`

List all directory contents sorted by time edited: `ls -alt`

List directory (wildcard matching): `ls *.txt`

List all files of type: `find . -name "*.txt" -print`

Go back to previous directory: `cd -`

Make (empty) directory: `mkdir sample-dirname`

Remove (empty) directory: `rmdir sample-dirname`

Remove directory with all contents: `rm -rf sample-dirname/`

Remove directory contents and keep directory: `rm -rf *`

Checkout directory: `cd sample-dirname`

Browsing directories: `pushd sample-dirname` / `popd` / `dirs` 
(see http://unix.stackexchange.com/a/77081)

## Symlinks
Create symlink: `ln -s source-dirname destination-dirname`

Update symlink: `ln -sfn source-dirname destination-dirname`

Remove symlink: `unlink sample-dirname`

- `-s`: Create a symbolic link.
- `-f`: If the target file already exists, then unlink it.
- `-F`: If the target file already exists and is a directory, then remove/overwrite it.
- `-h`: If the target file or directory is a symbolic link, do not follow it.
- `-n`: Same as `-h`, for compatibility with other `ln` implementations.

## Files
Make (empty) file: `touch sample-filename.txt`

Change creation date: `touch –t 201401011337 sample-filename.txt`

Change modified date: `touch –mt 201401011337 sample-filename.txt`

Duplicate file: `cp sample-filename.txt sample-filename-copy.txt`

Copy/Page folder with content: `cp -a folder/ new_folder`

Move/Rename file: `mv current-filename.txt new-filename.txt`

Move/Rename file and prompt before overwriting an existing file: `mv -i current-filename.txt new-filename.txt`

Remove file: `rm sample-filename.txt`

View file: `less sample-filename.txt` / `more sample-filename.txt`

Write to file (will overwrite existing content): `cat > sample-filename.txt` (quit with `ctrl+d`)

Search for a filename (not content!) in the current directory: `find sample-filename.txt`

Search for a string (not filename!) inside all files in the current directory: `ack "string" --php` ([documentation](https://beyondgrep.com/documentation/))

Search for a string inside all files in the current directory and subdrectories: `grep -r "string" *`

Search and replace within file: `sed -i '' 's/original-text/new-text/g' sample-filename.txt`

MD5 hash for files: `md5 sample-filename.txt` 

MD5 hash for folders: `tar c folder | md5sum`

Encrypt file: `openssl enc -aes-256-cbc -e -in sample-filename.txt -out sample-encrypted.txt`

Decrypt file: `openssl enc -aes-256-cbc -d -in sample-encrypted.txt -out sample-filename.txt`

## Server
Access via ssh: `ssh pi@192.168.0.0`

Copy file from server to local: `scp pi@192.168.0.0:/path/to/file.png ~/Desktop/` 
(use `-r` to recursively get complete folder)

Copy file from local to server: `scp ~/Desktop/file.png pi@192.168.0.0:/path/to/folder ` 
(use `-r` to recursively get complete folder)

Copy file from local to server: `rsync --exclude=".DS_Store" -vzcrSLh ~/Desktop/file.png pi@192.168.0.0:/path/to/folder`

Escape files with spaces in name like this: `/path/to/file\\\ name.png`

## System
Show disc space: `df -h`

Show disc space (inodes): `df -i`

Show disc space for current directory: `du -hs`

Current processes (also CPS usage): `top` or `htop`

Show running php processes: `ps aux | grep php`

Monitor error log (stream as file grows): `tail error.log -f -n 0`

## Apps
Start appliction: `open -a [name-of-programm]` e.g. `open -a firefox`

Open finder with current folder: `open .`

## Variables
Register variable: `export TESTING="Sample Text"`

Echo variable: `echo $TESTING`

Unset variable: `unset TESTING`

## Output & Redirects
Write to file: `echo "Hello" > hello.txt`

Append content from a file to another file: `cat file1.txt >> file2.txt`

Add the amount of lines, words, and characters to `file2.txt`: `cat file1.txt | wc | cat > file2.txt`

Sort the content of a file (like `cat`): `sort hello.txt`

Save to sorted content to a new file: `cat file1.txt | sort > sorted-file1.txt`

Sort and remove duplicates and save to a new file: `sort file1.txt | uniq > uniq-file1.txt`

## Functions
Calculate (returns only `int`): `echo $((123/2))`

## HTTP
Check site feedback: `ping google.com`

Show site IP: `dig +short google.com`

Show A Record: `dig a google.com` (Returns: `google.com.	43	IN	A	123.123.123.123` aka `public-name ttl internet record-type server-address`)

Webservice: https://www.whatsmydns.net/

Curl headers: `curl -I https://hofmannsven.com`

## Tools

### [Tree](http://mama.indstate.edu/users/ice/tree/tree.1.html)

Installation: `brew install tree`

### [HTTPie](https://httpie.org/)

Installation: `brew install httpie`

Usage:
```
http GET https://hofmannsven.test --verify=no
```

## Security
Fix OpenSSH Client Bug: https://www.digitalocean.com/community/questions/openssh-client-bug-cve-2016-0777-and-cve-2016-0778
