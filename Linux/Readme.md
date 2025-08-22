# Linux Notes

---

## Linux Permissions

### CHMOD - change read,write and execute permissions

this only applies to non-root users,
as root have all access and consideres as seperate entity altogether.

| User | Group | Other |
| ---- | ----- | ----- |
| rwx  | rwx   | rwx   |

this permission can be set using `chmod` command:
|permission|value|
|---|---|
|read |4|
|write|2|
|execute|1|
|no permission|0|

say for example we want:
user to rwx -> 4+2+1 = 7
group to rw -> 4+2+0 = 6
others to r -> 4+0+0 = 4

we use command like :
`chmod -R 764 filename.txt`
`-R` - recursively pass permisions to sub contents.

### CHOWN- change ownership of content

Now , to set this user and group ownership we use `chown`
let user: jack and group:IT access a file .
here user is unique , while group contains any user and gets same permissions as group.
`chmod user:group filename.txt`

example:
we can use `ls -l` to list contents as well as their permissions.
if there is a directory , it will show d at start.
`drwxrwxrwx 1 root root  152 Aug 22 21:16 React`
here first char is - which means its not a directory.
`-rwxrwxrwx 1 root root  217 Aug 22 21:17 README.md`

---

## ls - List Content

`ls` - list directories and files
`ls ,` - list content of current directory
`ls <path>` - list directories at path provided like ~/Downloads /home/user/Downloads

### flags :

`-l` - list contents along with their properties like read,write and execute permission, which user and group owns it , month day and time it was created or modified and name of directory/file.
`-a` - list hidden files
`-R` - list subdirectories as well.
`-s` - to list directories along with their size in blocks.

---

## Network

### ip addr

to list all network with configurations with ipaddress and so on.
`ip addr`
lo means loopback
wlo(x) means wifi
eth(x) means ethernet
`ip addr show {typeofnetwork}` specifically shows a certain network details like wlo1.

### ping

`ping <address>` to ping a certain address
`ping -c n <address>` this command pings `<address>` `n` times.

### nmcli - Network Manager CLI

this is useful to view , connect and analyze network interfaces on terminal

`nmcli device` - shows
DEVICE,TYPE,STATE,CONNECTION
wlo1,wifi,connected,wifi_name

`nmcli connection up <devicename>` to activate or turn on a device.

`nmcli device wifi list` - lists all wifi networks

`nmcli device wifi connect <SSID> password <password>` - to connect to a wifi connection with its ssid and password.

### ss

`ss -tlnp` - to lists services and ports there are listening to.
`-t`: display only tcp sockets,
`-l`: display listening sockets,
`-n`: dont resolve service names,
`-p`: show process using sockets,

---

### for archlinux

`sudo pacman -Syu` : to update full system
`S` sync databases from remote to local
`u` update changed packages
`y` allow/confirm all changes

`sudo pacman -S <package>` : to install a package/app/service

---

### file path of a command

`which <command>`, shows executable path of a command.

### show manual of a command

`man <command>`: shows manual for that command

### clear terminal

`clear` clears terminal.

### see commands history

`history` : shows previous commands user inputted.

### show currently logged in users

`who` shows user currently logged in or using system.

### grep filter output

`command | grep <filter>` : we use piping `|` to pass output to next command.
`grep` is used to filter lines which contains filter like regex , string ,etc.
`grep user` shows only lines containing the word user.

---

## Navigate system

### Current directory

`pwd` shows currently working directory user is in.

`~/` this is home directory of current user.

### Change directory

`cd directoryname` to change working directory, can use relative `./folder`, `folder` or absolute path `/home/user/Desktop/folder`.

### Move , Copy or Remove Content

`mv <source> <destination>`: moves files or folders source -> destination.
can have multiple sources but final path is considered as destination.
`cp <source> <destination>` copies files or folders source -> destination.can have multiple sources but final path is considered as destination.
both mv and cp commands we can use `-r` flag to also copy subdirectories and subfiles of parentfolder as well.
`rm <source>` : removes files and empty folder.
to remove folders/directories with its contents , we use `-r` flag.
