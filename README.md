# MyKaliSetup


Kali Linux 2021.3 Latest Version
Debian
UPDATED


ERASE KEYS:

dpkg-reconfigure openssh-server

FIX MISSING UPDATE:

sudo apt update --fix-missing

SUDO LOGIN:

sudo su

INSTALL SSH:

sudo apt install
sudo service ssh start
sudo service ssh status

ENABLE ROOT LOGIN:

sudo nano /etc/ssh/sshd_config
PermitRootLogin yes
sudo service ssh restart

TO MAKE SSH MORE SECURE:

sudo nano /etc/ssh/sshd_config
unhash port 
erase 22, replace with whatever number up to 6595
port 2900
then:
ssh root@192.168.1.3 -p 2900

THEN REBOOT SYSTEM:
sudo systemctl enable ssh


LOGIN TO ROOT:

sudo -i

ASUS BIOS:
On Start Up Press F2

Install GParted:

sudo apt install gparted

sudo apt update
sudo apt upgrade
sudo dist-upgrade

sudo passwd root
sudo passwd "User"

ENABLE BLUETOOTH ON RASP4:
sudo systemctl enable --now uart.servie
sudo systemctl enable --now bluetooth.service

REDIRECT AUDIO TO 3.5 JACK NOT HDMI:
 $ sudo amixer -c 0 set numid=3 1


ZSH Install:

To Change default Shell:sudo nan

chsh
/bin/zsh

logout, log back in, Shell is changed

OH MY ZSH Install:

Website: https://ohmyz.sh/

sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

Vi ~/.zshrc
Theme: "imajes"

Zsh-autosuggestion Install:
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

vi ~/.zshrc
scroll to pluggins
(git zsh-autosuggestions)

pluggin: zsh-autosuggestions

sudo adduser "justjoshin"
sudo gpasswd -a justjoshin adm
sudo gpasswd -a justjoshin sudo
sudo gpasswd -a justjoshin kismet

Sudoers:
sudo visudo /etc/sudoers

Scroll to bottom:

justjoshin  ALL=(ALL)        NOPASSWD:ALL
munkimind   ALL=(ALL)        NOPASSWD:ALL

Automatic Updates: getting raspbian updates

sudo apt install unattended-upgrades
sudoedit /etc/apt/apt.conf.d/50unattended-upgrades

Scroll to "origin=debian"
          "origin=debian"
Paste These Lines Right Under:

"origin=Raspbian,codename=$(distro_codename),label=Raspbian";
"origin=Raspberry Pi Foundation,codename=$(distro_codename),label=Raspberry Pi Foundation";

Install Sherlock: Username

Docker:

sudo apt install docker.io

docker help

Phoneinfoga:

sudo cp phoneinfoga /user/bin/

How to Use:

./phoneinfoga

./phoneinfoga scan -n 18282915149

Cryptr:File Encryption

git clone https://github.com/nodesocket/cryptr.git
ln -s "$PWD"/cryptr/cryptr.bash /usr/local/bin/cryptr

crypt encrypt "text.txt"

crypt decrypt "text.txt.aes"

raspi-config:
ssh 
display calibration

Display Config: Overscan

sudo nano /boot/config.txt

Lock User:
sudo passwd -l pi

Sudoers:
sudo visudo /etc/sudoers

Scroll to bottom:

justjoshin  ALL=(ALL)        NOPASSWD:ALL
munkimind   ALL=(ALL)        NOPASSWD:ALL

Automatic Updates: getting raspbian updates

sudo apt install unattended-upgrades
sudoedit /etc/apt/apt.conf.d/50unattended-upgrades

Scroll to "origin=debian"
          "origin=debian"
Paste These Lines Right Under:

"origin=Raspbian,codename=$(distro_codename),label=Raspbian";
"origin=Raspberry Pi Foundation,codename=$(distro_codename),label=Raspberry Pi Foundation";

Find Out What Is Running On System:
systemctl --type=service
systemctl --type=service --state=active

How To Disable Unused Programs:

sudo systemctl disable "program name"
or 
sudo systemctl disable "program" --now

How To Enable:
sudo systemctl enable 
Or sudo systemctl enable --now 

Firewall:

apt install ufw

sudo ufw allow 22/tcp comment "SSH"
sudo ufw allow 8080/tcp comment "Web Server"

sudo ufw enable 

SSH:

sudoedit /etc/ssh/sshd_config

Scroll down under maxsessions 10

AllowUsers justjoshin,munkimind 

Login Protection:

apt install fail2ban

sudoedit /etc/fail2ban/jail.local

[DEFAULT]
bantime = 1h
banaction = ufw

[sshd]
enabled = true

sudo systemctl enable --now fail2ban
sudo sysemctl restart sshd


Raspbian Customization:

DISABLE AUTOLOGIN:

cd /etc/lightdm

sudo nano lightdm.conf
Scroll to autologin-user=pi
# it out
then reboot

Make sure you added users correctly:

cat /etc/passwd

MAKE IP STATIC:

sudo nano /etc/dhcpcd.conf
interface wlan0
static ip address=192.168.1.176/24
static router=192.168.1.1
static domain_name_servers=8.8.8.8

Yersinia: Hacking Tool
apt install yersinia
yersinia -G

ettercap: Hacking Tool
apt install ettercap-graphical
sudo ettercap -G

(Note) -G gives you a graphical interface


Driver Installation for 3.5 LCD

sudo rm -rf LCD-show
git clone https://github.com/goodtft/LCD-show.git
chmod -R 755 LCD-show
cd LCD-show/
sudo /LCD35-show


Find Out What Shells Are Installed: 

cat /etc/shells

Find Out Version of OS:
uname -r 

or 

echo "$(uname -s)_$(uname -m)"

$path: Find out What Path

echo $PATH

LibreOffice:

sudo apt install libreoffice

Create Txt Document:

cd "for where you want to store doc"

cat > "Name of File.txt"

ECDSA key fingerprint is SHA256: on 192.168.1.176
To Delete or Clear this: ssh-keygen -R 192.168.1.176

X11VNC:

sudo apt install x11vnc

Passwd:

x11vnc -storepasswd

then:

x11vnc -nache 10 -auth guess -nap -forever -loop -repeat -rfbauth /root/.vnc/passwd -rfbport 5900

WORDLISTS:
Navigate to wordlists by:

cd /usr/share/wordlists

cd

Copies rockyou.txt to home or root

cp /usr/share/wordlists/rockyou.txt rockyou.txt

Creates Passwd List 8-63 Characters Saves File in wparockyou.txt:

sudo grep -x '.\{8,63\}' rockyou.txt > wparockyou.txt

wordcount in lists:

wc -l rockyou.txt

To Find Passwds:

grep "Moxxi" rockyou.txt



GZIP:

sudo apt install gzip

To Unzip Files:

sudo gzip -d rockyou.txt.gz

Alias: Command Shortcuts

List of all Alias:

alias

alias zshconfig

alias hackwifi "wifite"

Make sure RFMON is Enabled run:
'airmon-ng start wlan0 <#>'

Reconfigure SSH Keys:

cd /etc/ssh

dpkg-reconfigure openssh-server

Tilix Install: Up to 4 Terminals at once

sudo apt install tilix

Pi-Hole: Ad Blocker/Browser with Tor

curl -sSL https://install.pi-hole.net | bash

Raspberry Pi Kernel Upgrade:
rpi.sh

git clone --depth 1 https://github.com/raspberrypi/linux ${basedir}/kernel

would change to:

git clone -b rpi-3.13.y --depth 1 https://github.com/raspberrypi/linux ${basedir}/kernel

rpi-wiggle 
size=3000 # size of image in megabytes

Then introduce files into the scripts directory

# rpi-wiggle
mkdir -p ${basedir}/root/scripts
wget https://raw.github.com/dweeber/rpiwiggle/master/rpi-wiggle -O ${basedir}/root/scripts/rpi-wiggle.sh
chmod 755 ${basedir}/root/scripts/rpi-wiggle.sh

then boot pi run script in/scripts/ to automaticallyresize the partitions

root@kali:~# cd /scripts
root@kali:/scripts# ./rpi-wiggle.sh

RASPI SSH:
root@amazon:~/kali-arm-build-scripts# ./rpi.sh custom
helps fix ssh bug

HOW TO FIND IP ADDRESS FOR ANY WEBSITE:

dmitry -i bandit.labs.overthewire.org
176.9.9.172

PYTHON:
PYTHON.ORG
LATEST VERION 3.9
DOWNLOAD SOURCE CODE
EXTRCT HERE
OPEN FOLDER AND OPEN TERMINAL IN FOLDER

ls
./configure
./configure --enable-optimizations
make
make install
to access type:
python3.9 -v

WHEN OPENING CERTAIN FILES WITH CAT THAT HAVE SPACES:
spaces in this filename 
cat ./spaces\ in\ this\ filename\
enter
enter

BETTERCAP INSTALL:

sudo apt install bettercap

HOW TO USE:

bettercap
net.probe on
net.recon on
net.sniff on 
net.show:shows everything on the network your on
arp.spoof: tells everything on the network to run through the pi



TO FIND HUMAN READABLE ONLY FILES:

find . -type f | xargs filecat

TO MAKE FILE EXECUTABLE: 

sudo chmod u+x pihole.sh
sudo chmod u+x "filename" no quotes

PIHOLE INSTALL:

PIHOLE.SH FILE:

#!/bin/bash

# https://github.com/pi-hole/docker-pi-hole/blob/master/README.md

docker run -d \
    --name pihole \
    -p 53:53/tcp -p 53:53/udp \
    -p 80:80 \
    -p 443:443 \
    -p 8080:8080 \
    -e TZ="America/Chicago" \
    -v "$(pwd)/etc-pihole/:/etc/pihole/" \
    -v "$(pwd)/etc-dnsmasq.d/:/etc/dnsmasq.d/" \
    --dns=127.0.0.1 --dns=1.1.1.1 \
    --restart=unless-stopped \
    thenetworkchuck/networkchuck_pihole

printf 'Starting up pihole container '
for i in $(seq 1 20); do
    if [ "$(docker inspect -f "{{.State.Health.Status}}" pihole)" == "healthy" ] ; then
        printf ' OK'
        echo -e "\n$(docker logs pihole 2> /dev/null | grep 'password:') for your pi-hole: https://${IP}/admin/"
        exit 0
    else
        sleep 3
        printf '.'
    fi

    if [ $i -eq 20 ] ; then
        echo -e "\nTimed out waiting for Pi-hole start, consult check your container logs for more info (\`docker logs pihole\`)"
        exit 1
    fi
done;

CREATE FILE:

sudo nano "file name"

CREATE FILE PIHOLE.SH
PASTE SCRIPT IN FILE
MAKE EXECUTABLE

sudo ./pihole.sh


Shortcuts:

ADD TERMINAL RIGHT: SUPER + RIGHT
ADD TERMINAL DOWN: SUPER + DOWN
SWITCH TERMINALS: ALT + ARROWS
OPEN FILE EXPLORER: SUPER + E


Copy: Ctrl+Shift=C
Paste: Ctrl+Shift+V
Paste Selection: Shift=Insert
Reset and Clear Terminal: Ctrl+Esc
Switch Tabs: Ctrl+Tab
Find: Ctrl+Shift+F
Select All: Ctrl+Shift+A
Terminal: Ctrl+Shift+T

KALI LINUX COMMAND LIST:

Kali Linux Commands
	

Function:

A:
 
apt-get
	

Search for and install software packages (Debian)

aptitude
	

Search for and install software packages (Debian)

aspell
	

Spell Checker

awk
	

Find and Replace text, database sort/validate/index

B:

basename
	

Strip directory and suffix from filenames

bash
	

GNU Bourne-Again Shell

bc
	

Arbitrary precision calculator language

bg
	

Send to background

break
	

Exit from a loop

builtin
	

Run a shell builtin

bzip2
	

Compress or decompress named files

C:

cal
	

Display a calendar

case
	

Conditionally perform a command

cat
	

Concatenate and print (display) the content of files

cd
	

Change Directory

cfdisk
	

Partition table manipulator for Linux

chgrp
	

Change group ownership

chmod
	

Change access permissions

chown
	

Change file owner and group

chroot
	

Run a command with a different root directory

chkconfig
	

System services (runlevel)

cksum
	

Print CRC checksum and byte counts

clear
	

Clear terminal screen

cmp
	

Compare two files

comm
	

Compare two sorted files line by line

command
	

Run a command – ignoring shell functions

continue
	

Resume the next iteration of a loop

cp
	

Copy one or more files to another location

cron
	

Daemon to execute scheduled commands

crontab
	

Schedule a command to run at a later time

csplit
	

Split a file into context-determined pieces

cut
	

Divide a file into several parts

D:

date
	

Display or change the date and time

dc
	

Desk Calculator

dd
	

Convert and copy a file, write disk headers, boot records

ddrescue
	

Data recovery tool

declare
	

Declare variables and give them attributes

df
	

Display free disk space

diff
	

Display the differences between two files

diff3
	

Show differences among three files

dig
	

DNS lookup

dir
	

Briefly list directory contents

dircolors
	

Colour setup for ls’

dirname
	

Convert a full pathname to just a path

dirs
	

Display list of remembered directories

dmesg
	

Print kernel &amp; driver messages

du
	

Estimate file space usage


E:

echo
	

Display message on screen

egrep
	

Search files for lines that match an extended expression

eject
	

Eject removable media

enable
	

Enable and disable builtin shell commands

env
	

Environment variables

ethtool
	

Ethernet card settings

eval
	

Evaluate several commands/arguments

exec
	

Execute a command

exit
	

Exit the shell

expect
	

Automate arbitrary applications accessed over a terminal

expand
	

Convert tabs to spaces

export
	

Set an environment variable

expr
	

Evaluate expressions

F:

false
	

Do nothing, unsuccessfully

fdformat
	

Low-level format a floppy disk

fdisk
	

Partition table manipulator for Linux

fg
	

Send job to foreground

fgrep
	

Search files for lines that match a fixed string

file
	

Determine file type

find
	

Search for files that meet a desired criteria

fmt
	

Reformat paragraph text

fold
	

Wrap text to fit a specified width

for
	

Expand words, and execute commands

format
	

Format disks or tapes

free
	

Display memory usage

fsck
	

File system consistency check and repair

ftp
	

File Transfer Protocol

function
	

Define Function Macros

fuser
	

Identify/kill the process that is accessing a file

G:

gawk
	

Find and Replace text within files

getopts
	

Parse positional parameters

grep
	

Search files for lines that match a given pattern

groupadd
	

Add a user security group

groupdel
	

Delete a group

groupmod
	

Modify a group

groups
	

Print group names a user is in

gzip
	

Compress or decompress named files

H:

hash
	

Remember the full pathname of a name argument

head
	

Output the first part of files

help
	

Display help for a built-in command

history
	

Command History

hostname
	

Print or set system name

I:

iconv
	

Convert the character set of a file

id
	

Print user and group id’s

if
	

Conditionally perform a command

ifconfig
	

Configure a network interface

ifdown
	

Stop a network interface

ifup
	

Start a network interface up

import
	

Capture an X server screen and save the image to file

install
	

Copy files and set attributes

J:

jobs
	

List active jobs

join
	

Join lines on a common field

K:

kill
	

Stop a process from running

killall
	

Kill processes by name

L:

less
	

Display output one screen at a time

let
	

Perform arithmetic on shell variables

ln
	

Create a symbolic link to a file

local
	

Create variables

locate
	

Find files

logname
	

Print current login name

logout
	

Exit a login shell

look
	

Display lines beginning with a given string

lpc
	

Line printer control program

lpr
	

Off line print

lprint
	

Print a file

lprintd
	

Abort a print job

lprintq
	

List the print queue

lprm
	

Remove jobs from the print queue

ls
	

List information about files

lsof
	

List open files

M:

make
	

Recompile a group of programs

man
	

Help manual

mkdir
	

Create new folders

mkfifo
	

Make FIFOs (named pipes)

mkisofs
	

Create an hybrid ISO9660/JOLIET/HFS filesystem

mknod
	

Make block or character special files

more
	

Display output one screen at a time

mount
	

Mount a file system

mtools
	

Manipulate MS-DOS files

mtr
	

Network diagnostics (traceroute/ping)

mv
	

Move or rename files or directories

mmv
	

Mass Move and rename files
 
es

N:

netstat
	

Networking information

nice
	

Set the priority of a command or job

nl
	

Number lines and write files

nohup
	

Run a command immune to hangups

notify-send
	

Send desktop notifications

nslookup
	

Query Internet name servers interactively

O:

open
	

Open a file in its default application

op
	

Operator access

P:

passwd
	

Modify a user password

paste
	

Merge lines of files

pathchk
	

Check file name portability

ping
	

Test a network connection

pkill
	

Stop processes from running

popd
	

Restore the previous value of the current directory

pr
	

Prepare files for printing

printcap
	

Printer capability database

printenv
	

Print environment variables

printf
	

Format and print data

ps
	

Process status

pushd
	

Save and then change the current directory

pwd
	

Print Working Directory

Q:

quota
	

Display disk usage and limits

quotacheck
	

Scan a file system for disk usage

quotactl
	

Set disk quotas

R:

ram
	

ram disk device

rcp
	

Copy files between two machines

read
	

Read a line from standard input

readarray
	

Read from stdin into an array variable

readonly
	

Mark variables/functions as readonly

reboot
	

Reboot the system

rename
	

Rename files

renice
	

Alter priority of running processes

remsync
	

Synchronize remote files via email

return
	

Exit a shell function

rev
	

Reverse lines of a file

rm
	

Remove files

rmdir
	

Remove folders

rsync
	

Remote file copy (Synchronize file trees)

S:

screen
	

Multiplex terminal, run remote shells via ssh

scp
	

Secure copy (remote file copy)

sdiff
	

Merge two files interactively

sed
	

Stream Editor

select
	

Accept keyboard input

seq
	

Print numeric sequences

set
	

Manipulate shell variables and functions

sftp
	

Secure File Transfer Program

shift
	

Shift positional parameters

shopt
	

Shell Options

shutdown
	

Shutdown or restart linux

sleep
	

Delay for a specified time

slocate
	

Find files

sort
	

Sort text files

source
	

Run commands from a file

split
	

Split a file into fixed-size pieces

ssh
	

Secure Shell client (remote login program)

strace
	

Trace system calls and signals

su
	

Substitute user identity

sudo
	

Execute a command as another user

sum
	

Print a checksum for a file

suspend
	

Suspend execution of this shell

symlink
	

Make a new name for a file

sync
	

Synchronize data on disk with memory

T:

tail
	

Output the last part of file

tar
	

Tape Archiver

tee
	

Redirect output to multiple files

test
	

Evaluate a conditional expression

time
	

Measure Program running time

times
	

User and system times

touch
	

Change file timestamps

top
	

List processes running on the system

traceroute
	

Trace Route to Host

trap
	

Run a command when a signal is set(bourne)

tr
	

Translate, squeeze, and/or delete characters

true
	

Do nothing, successfully

tsort
	

Topological sort

tty
	

Print filename of terminal on stdin

type
	

Describe a command

U:

ulimit
	

Limit user resources

umask
	

Users file creation mask

umount
	

Unmount a device

unalias
	

Remove an alias

uname
	

Print system information

unexpand
	

Convert spaces to tabs

uniq
	

Uniquify files

units
	

Convert units from one scale to another

unset
	

Remove variable or function names

unshar
	

Unpack shell archive scripts

until
	

Execute commands (until error)

uptime
	

Show uptime

useradd
	

Create new user account

usermod
	

Modify user account

users
	

List users currently logged in

uuencode
	

Encode a binary file

uudecode
	

Decode a file created by uuencode

V:

v
	

Verbosely list directory contents (ls -l -b’)

vdir
	

Verbosely list directory contents (ls -l -b’)

vi
	

Text Editor

vmstat
	

Report virtual memory statistics

W:

wait
	

Wait for a process to complete

watch
	

Execute/display a program periodically

wc
	

Print byte, word, and line counts

whereis
	

Search the user’s $path, man pages and source files for a program

which
	

Search the user’s $path for a program file

while
	

Execute commands

who
	

Print all usernames currently logged in

whoami
	

Print the current user id and name (id -un’)

wget
	

Retrieve web pages or files via HTTP, HTTPS or FTP

write
	

Send a message to another user

X:

xargs
	

Execute utility, passing constructed argument lists

xdg-open
	

Open a file or URL in the user’s preferred application

Y:

yes
	

Print a string until interrupted













































