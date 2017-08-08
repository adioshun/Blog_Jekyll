


- GPU Monitoring : `apt-get install nmon' 

- Job Monitoring and notification : [Hyperdash](https://hyperdash.io/), `pip install hyperdash && hyperdash login`

## zsh변경

```
sudo apt-get install zsh curl
chsh -s `which zsh`
sudo curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```
> zsh가 느리게 시작 할때 `sudo rm -rf /private/var/log/asl*.as`

[참고](https://nolboo.kim/blog/2015/08/21/oh-my-zsh/)



# Tip

## 공간 환보
```
apt-get clean

pip clean?
```
