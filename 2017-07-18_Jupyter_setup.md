### Jupyter Configuration

```bash
jupyter notebook --generate-config --allow-root
vi /root/.jupyter/jupyter_notebook_config.py
```
`jupyter_notebook_config.py` 설정파일
```
#c = get_config()
c.NotebookApp.ip = '*'  #L158
c.NotebookApp.open_browser = False # L201 원격접속으로 활용할 것이기 때문에 비활성화 시켰다.
c.NotebookApp.port = 8585 # L213 포트를 설정해준다. 기본포트로 8888이 자동 배정된다.
c.NotebookApp.password = 'sha1:a8dee43a3a44:b18f1ad149a60efb4838da44cf127985d64a5e70' # L210 python 실행후 from notebook.auth import passwd; passwd\(\)
c.NotebookApp.notebook_dir = '/home/adioshun/Jupyter' # L195 기본 디렉터리를 지정시켜준다.
```

> 실행:jupyter notebook --allow-root

jupyter 테마: [#1](https://github.com/powerpak/jupyter-dark-theme), [#2](http://haanjack.github.io/jupyter/theme/2016/03/08/jupyter-theme.html), [#3](https://github.com/dunovank/jupyter-themes)

### Jupyter Lab설치

Unonffical
```
# you will need jupyter notebook >= v4.2
pip3 install jupyterlab
jupyter serverextension enable --py jupyterlab --sys-prefix
jupyter lab
```
### Jupyter Extension설치
##### Official:[ref](https://docs.continuum.io/anaconda/jupyter-notebook-extensions)
```
conda install nb_conda -c conda-forge
# conda install nb_conda
# conda install -c anaconda-nb-extensions nbpresent

```
> UnsatisfiableError: [solved](https://github.com/ContinuumIO/anaconda-issues/issues/1423)


##### Unofficial:[ref](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/install.html)
```
conda install -c conda-forge jupyter_contrib_nbextensions
#pip install https://github.com/ipython-contrib/jupyter_contrib_nbextensions/tarball/master
jupyter contrib nbextension install --user
```
[참고](https://github.com/ipython-contrib/jupyter_contrib_nbextensions)

### Jupyter 다중커널설정
```
# conda2 OR 3 install 

conda create -n pyton3 python=3

jupyter kernelspec list #설치된 커널 확인 
conda install notebook ipykernel
ipython kernel install --user
```

> [Docker 이미지로 설치한 Jupyter에 커널 추가하기](http://mazdah.tistory.com/784)

#### 2. Python 용 R 설치 \(/w conda\)

```bash
conda install -c r r-irkernel
conda install -c r r-essentials
```

###### ipython에서 R 패지키 설치 방법 \(R 콘솔에서 실행??\)

sudo apt-get install libcurl4-openssl-dev
sudo apt-get install libssl-dev
```
#R쉘진입
install.packages(c('repr', 'IRdisplay', 'evaluate', 'crayon', 'pbdZMQ', 'devtools', 'uuid', 'digest'))
devtools::install_github('IRkernel/IRkernel')
IRkernel::installspec()
```

> 패키지설치시: install.packages("ldavis", "/home/user/anaconda3/lib/R/library")
> [메뉴얼필독](https://www.r-bloggers.com/jupyter-and-r-markdown-notebooks-with-r/amp/)

-- 
# Jupyter Tips

- [28 Jupyter Notebook tips, tricks and shortcuts](https://www.dataquest.io/blog/jupyter-notebook-tips-tricks-shortcuts/)
