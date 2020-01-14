# 2020 Python Engineering Practice  on mac OS



技术在不断推进， 信息具有时间性，许多设计/实现都有着当时因缘际会的因素的而造就，随着时间变化，设计实现都有了更好的替代。因此写一下2020年这个时候，python相关的一些工程实践，供大家批判性的参考，少走弯路，不要摸着石头过河了. 



###  开发环境限制条件 

* mac OS    



###经验0:    只需要精深如何使用pytho3,  不要看python2 的任何东西 ;

​			   某些mac OS系统可能是自带的是python2.x ， 不要担心，请继续向下看.



# python编程一定要上虚拟化环境:  建立两层虚拟环境

##  1. OS级虚拟环境:  pyenv

###经验1.0   最好的os级虚拟环境是pyenv，   mac OS  通过brew 安装pyenv ， 不管mac OS里面装的是什么python 版本，都不要紧 ;



###经验1.1  有些奇怪的书籍或者文章会推荐anaconda, ipython, jupyter notebook等给新入门者，这些名词的意思不一样，也用于不同用途，即使是科学计算，我也建议安装正常的python包，然后用 pip来管理你所需要的其他包，在我的指引下，你不会担心编译的问题,  也可以轻松达到懒人包的效果; 



###经验1.2   不要上当说需要删除现有操作系统中的python， 也不要通过源码包自己来编译，相信我, Linux老鸟也不想编译源码安装；

在编译的时候会遇到各种要安装gcc , 或者zlib  openssl等各种依赖的情况，少了编译参数就可能在遇到具体的用python 的软件的时候要重新编译 python （特别是在ubuntu 系统上）;



###经验1.3   安装完成 pyenv 之后， 选择你需要的python 版本 在pyenv里面安装就好了



###经验1.4   在pyenv里，设置global,  system , local 不同层次下如何切换，和使用你所需要的python 版本

```bash
#查看pyenv上当前可安装的 python 版本 
$pyenv install --list
```



## 2. 彻底告别python2 python3 这种启动方式

###经验1.5 在.py文件里，不要再用 python2, python3 指定绝对路径了, 改为使用如下方式

```python
#!/usr/bin/env python
```


##  3. Project级虚拟环境:  python -m venv  (不要再用virtualenv)

###经验1.5    不要再使用virtualenv了，从python 3.5 开始自带 venv模块， 即可创建虚拟环境

```bash
$python -m venv yourenvpath
```

为每一个项目的总工程目录（也可以公用，看你的需要）建立虚拟环境，把需要的包装在虚拟环境里面，不干扰os 级别的虚拟环境;  通过如下方式进入项目虚拟环境和退出: 

```bash
#激活虚拟环境
$source  yourenvpath/bin/activate  
#退出虚拟环境
(yourenvpathname)$deactivate
```



###经验1.6   用 autoenv 来实现自动载入项目所需要虚拟环境，实现进入目录则自动激活虚拟环境

```bash
#下载 autoenv
git clone git://github.com/kennethreitz/autoenv.git ~/.autoenv
# 配置autoenv 到bash自动加载
echo 'source ~/.autoenv/activate.sh' >> ~/.bash_profile
# 在当前shell先来一把 ,假设你用的是bash + mac OS  请要注意mac os的特殊性，不要写在 .bashrc里 , 如果你用的zsh 我想你一定知道要改哪个文件
source ~/.bash_profile
```

进入项目目录配置 .env文件来实现进入项目目录的自动化:

```bash
# 进入项目目录 假设为projectpath
echo "source venv/bin/activate" > projectpath/.env	

```

下次进入项目目录就会提示是否激活，再次进入时不会再提示.




