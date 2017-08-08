


- GPU Monitoring : `apt-get install nmon' 

- Job Monitoring and notification : [Hyperdash](https://hyperdash.io/), `pip install hyperdash && hyperdash login`
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

[설치](http://code4rain.tistory.com/1169527180), [자동설치 스크립트](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=tmux+install+script)

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
## set mouse for tmux 1.8 as shipped with Ubuntu 14.04
set -g mode-mouse on
set -g mouse-resize-pane on
set -g mouse-select-pane on
set -g mouse-select-window on
```

## 4windows Startup

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
