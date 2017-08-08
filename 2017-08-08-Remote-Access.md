## xrdp 원격 접속

#### GUI Desttop 환경설치
```
$ sudo apt-get install aptitude tasksel
$ sudo tasksel install gnome-desktop --new-install
```


### 원격 접속 툴
```
apt-get install xrdp
/etc/xrdp/xrdp.ini

[xrdp1]
name=Active Local Login
lib=libvnc.so
username=
password=ask
ip=127.0.0.1
port=5900

service xrdp restart
```
---
### VNC  원격 접속
###### Server side
```
sudo apt-get install -y tightvncserver
vncserver
```
vim .vnc/xstartup

```bash
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &

metacity &
gnome-settings-daemon &
gnome-panel &
```

###### client side
- `nc localhost 5901 #port open check`
---

### X11 Forwarding

```
# ~/.ssh/config file have these lines:
Host *
  ForwardAgent yes
  ForwardX11 yes
```

###### Server Side 
```
sudo apt-get install xauth
vi /etc/ssh/sshd_config  # X11 관련 3줄 Uncomment
service sshd restart

$ echo $DISPLAY  # export DISPLAY=localhost:10.0
ls -l ~/.Xauthority # Check user ID
xclock # it will show clock
```

### make connection
```
ssh -v -X -C xxx@xxx
sudo apt-get insatll spyder3 #conda install spyder
```

> No Qt bindings could be found : `pip3 install pyqt5`

> libGL.so.1: cannot open shared object file: `apt-get --reinstall install libgl1-mesa-glx`

> libsmime3.so: cannot open shared object file: `apt-get install libnss3-dbg`

> libasound.so.2: cannot open shared object file: `sudo apt-get install libasound2`

> libXtst.so.6: cannot open shared object file: `sudo apt-get install libxtst6`

### Chrome RND
http://timbot-inc.blogspot.com/2015/11/cloud-workstation-howto-chromebook.html
