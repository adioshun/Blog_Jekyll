

## Monitoring

- CPU 
	- htop : `sudo apt-get install htop`
	- nmon : `sudo apt-get install nmon`

- GPU Monitoring : 
	- `nvidia-smi -l 2` : `Failed to initialize NVML: Driver/library version mismatch` 에러시 `Reboot`
	- gpustat : `sudo pip install gpustat`, `watch --color -n1.0 gpustat`[[참고]](https://github.com/wookayin/gpustat)
	- glances : `sudo pip install glances[gpu]`, `sudo glances` (n, z, d)
		- `wget -O- https://bit.ly/glances | /bin/bash` [[홈페이지]](https://pypi.python.org/pypi/Glances)
	- intel-gpu-tools : `sudo apt-get install intel-gpu-tools`, `intel_gpu_top`

![](http://i.imgur.com/XjyHkIF.png)

- Job Monitoring and notification 
	- [Hyperdash](https://hyperdash.io/): `pip install hyperdash && hyperdash login`

![](http://i.imgur.com/QCEGtYx.png)

---

## zsh변경

```
sudo apt-get install zsh curl
chsh -s `which zsh`
sudo curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```
> zsh가 느리게 시작 할때 `sudo rm -rf /private/var/log/asl*.as`

> [oh-my-zsh](https://nolboo.kim/blog/2015/08/21/oh-my-zsh/)

---

## TMUX

> [홈페이지](https://github.com/tmux/tmux/wiki), [설치](http://code4rain.tistory.com/1169527180), [자동설치 스크립트](https://gist.github.com/bbelgodere/f77ee5e37ca661ad10ebe1f00020a8fd)

버젼확인 : tmux -V

```
apt-get install tmux
tmux new -s <원하는 이름>
```

	- Ctrl+j를 누른 후에 | 를 누르면 좌우로 분할되고
	- Ctrl+j를 누른 후에 - 를 누르면 상하로 분할됩니다.,
	- 미리 창 분활 해놓기 : [Tmuxinator](https://github.com/tmuxinator/tmuxinator)

출처: http://code4rain.tistory.com/1169527180 [codeRain's Life Blog]


## Mouse Support 

touch /root/.tmux.conf

```
## set mouse for tmux 2.1 as shipped with Ubuntu 14.04
set-option -g mouse on 

bind -n WheelUpPane   select-pane -t= \; copy-mode -e \; send-keys -M
bind -n WheelDownPane select-pane -t= \;                 send-keys -M

# Set the default terminal mode to 256color mode
set -g default-terminal "screen-256color"

# enable activity alerts
setw -g monitor-activity on
set -g visual-activity on

# Center the window list
set -g status-justify centre


```

```
# Use mouse for 1.8
setw -g mode-mouse on
set -g mouse-select-window on
set -g mouse-select-pane on
set -g mouse-resize-pane on
set -g mouse-utf on
```

## 4-windows Startup

script `start_tmux.sh`

```
echo 'start tmux'
#set session name
export SESSION=tmux
tmux -2 new-session -d -s $SESSION 
tmux split-window -v -t $SESSION  
tmux split-window -v -t $SESSION    
tmux split-window -h -t $SESSION  
  
tmux attach -t $SESSION
```

> [tmux shortcuts & cheatsheet](https://gist.github.com/MohamedAlaa/2961058)













# Tip

## 공간 환보
```
apt-get clean

pip clean?
```
