# 2020 Python Engineering Practice  on mac OS



技术在不断推进， 信息具有时间性，许多设计/实现都有着当时因缘际会的因素的而造就，随着时间变化，设计实现都有了更好的替代。因此写一下2020年这个时候，python相关的一些工程实践，供大家批判性的参考，少走弯路，不要摸着石头过河了. 


   * [2020 Python Engineering Practice  on mac OS](#2020-python-engineering-practice--on-mac-os)
         * [开发环境限制条件](#开发环境限制条件)
         * [经验0:    只需要精深如何使用pytho3,  不要看python2 的任何东西 ;](#经验0----只需要精深如何使用pytho3--不要看python2-的任何东西-)
   * [python编程一定要上虚拟化环境:  建立两层虚拟环境](#python编程一定要上虚拟化环境--建立两层虚拟环境)
      * [1. OS级虚拟环境:  pyenv](#1-os级虚拟环境--pyenv)
         * [经验1.0   最好的os级虚拟环境是pyenv，   mac OS  通过brew 安装pyenv ， 不管mac OS里面装的是什么python 版本，都不要紧 ;](#经验10---最好的os级虚拟环境是pyenv---mac-os--通过brew-安装pyenv--不管mac-os里面装的是什么python-版本都不要紧-)
         * [经验1.1  有些奇怪的书籍或者文章会推荐anaconda, ipython, jupyter notebook等给新入门者，这些名词的意思不一样，也用于不同用途，即使是科学计算，我也建议安装正常的python包，然后用 pip来管理你所需要的其他包，在我的指引下，你不会担心编译的问题,  也可以轻松达到懒人包的效果;](#经验11--有些奇怪的书籍或者文章会推荐anaconda-ipython-jupyter-notebook等给新入门者这些名词的意思不一样也用于不同用途即使是科学计算我也建议安装正常的python包然后用-pip来管理你所需要的其他包在我的指引下你不会担心编译的问题--也可以轻松达到懒人包的效果)
         * [经验1.2   不要上当说需要删除现有操作系统中的python， 也不要通过源码包自己来编译，相信我, Linux老鸟也不想编译源码安装；](#经验12---不要上当说需要删除现有操作系统中的python-也不要通过源码包自己来编译相信我-linux老鸟也不想编译源码安装)
         * [经验1.3   安装完成 pyenv 之后， 选择你需要的python 版本 在pyenv里面安装就好了](#经验13---安装完成-pyenv-之后-选择你需要的python-版本-在pyenv里面安装就好了)
         * [经验1.4   在pyenv里，设置global,  system , local 不同层次下如何切换，和使用你所需要的python 版本](#经验14---在pyenv里设置global--system--local-不同层次下如何切换和使用你所需要的python-版本)
      * [2. 彻底告别python2 python3 这种启动方式](#2-彻底告别python2-python3-这种启动方式)
         * [经验1.5 在.py文件里，不要再用 python2, python3 指定绝对路径了, 改为使用如下方式](#经验15-在py文件里不要再用-python2-python3-指定绝对路径了-改为使用如下方式)
      * [3. Project级虚拟环境:  python -m venv  (不要再用virtualenv)](#3-project级虚拟环境--python--m-venv--不要再用virtualenv)
         * [经验1.5    不要再使用virtualenv了，从python 3.5 开始自带 venv模块， 即可创建虚拟环境](#经验15----不要再使用virtualenv了从python-35-开始自带-venv模块-即可创建虚拟环境)
         * [经验1.6   用 autoenv 来实现自动载入项目所需要虚拟环境，实现进入目录则自动激活虚拟环境](#经验16---用-autoenv-来实现自动载入项目所需要虚拟环境实现进入目录则自动激活虚拟环境)
         * [PlayGround: jupyter notebook  (暂时不要pyCharm 等IDE, 不要iPython 等交互式命令行)](#playground-jupyter-notebook--暂时不要pycharm-等ide-不要ipython-等交互式命令行)

###  开发环境限制条件 

* mac OS    



### 经验0:    只需要精深如何使用pytho3,  不要看python2 的任何东西 ;

​			   某些mac OS系统可能是自带的是python2.x ， 不要担心，请继续向下看.



# python编程一定要上虚拟化环境:  建立两层虚拟环境

##  1. OS级虚拟环境:  pyenv

### 经验1.0   最好的os级虚拟环境是pyenv，   mac OS  通过brew 安装pyenv ， 不管mac OS里面装的是什么python 版本，都不要紧 ;
Linux 也可以，windows不建议.

> pyenv 安装  https://github.com/pyenv/pyenv-installer

```bash
$curl https://pyenv.run | bash
```

> pyenv project :  https://github.com/pyenv/pyenv


### 经验1.1  有些奇怪的书籍或者文章会推荐anaconda, ipython, jupyter notebook等给新入门者，这些名词的意思不一样，也用于不同用途，即使是科学计算，我也建议安装正常的python包，然后用 pip来管理你所需要的其他包，在我的指引下，你不会担心编译的问题,  也可以轻松达到懒人包的效果; 



### 经验1.2   不要上当说需要删除现有操作系统中的python， 也不要通过源码包自己来编译，相信我, Linux老鸟也不想编译源码安装；

在编译的时候会遇到各种要安装gcc , 或者zlib  openssl等各种依赖的情况，少了编译参数就可能在遇到具体的用python 的软件的时候要重新编译 python （特别是在ubuntu 系统上）;

> Linux系统上注意安装依赖
```bash
$sudo yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
```

> ModuleNotFoundError: No module named '_ctypes'
> $ sudo  yum install libffi-devel -y
>zipimport.ZipImportError: can't decompress data; zlib not available
make: *** [install] Error 1
[opc@hostjp-01 ~]$
[opc@hostjp-01 ~]$
[opc@hostjp-01 ~]$
[opc@hostjp-01 ~]$ sudo yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel


### 经验1.3   安装完成 pyenv 之后， 选择你需要的python 版本 在pyenv里面安装就好了



### 经验1.4   在pyenv里，设置global,  system , local 不同层次下如何切换，和使用你所需要的python 版本

```bash
#查看pyenv上当前可安装的 python 版本 
$pyenv install --list
```



## 2. 彻底告别python2 python3 这种启动方式

### 经验1.5 在.py文件里，不要再用 python2, python3 指定绝对路径了, 改为使用如下方式

```python
#!/usr/bin/env python
```


##  3. Project级虚拟环境:  python -m venv  (不要再用virtualenv)

### 经验1.5    不要再使用virtualenv了，从python 3.5 开始自带 venv模块， 即可创建虚拟环境

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



### 经验1.6   用 autoenv 来实现自动载入项目所需要虚拟环境，实现进入目录则自动激活虚拟环境

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

### PlayGround: jupyter notebook  (暂时不要pyCharm 等IDE, 不要iPython 等交互式命令行)

如何执行，python 代码片段？  最好的不是要 vim (虽然我在用vim写这个部分的笔记),
但即使是unix老鸟，也不想在命令行下面作python练习，熟悉命令是一方面(虽然你eventually的会使用vim)
关键在于它让你偏离了目标，尽快的上手开始coding in python.

在CLI (command line interface) 下coding 虽然看起来很酷,
但是会让你浪费很多的时间，而且写出代码的成果不能保存，不能来回调试修改已经写过的代码，
你可能需要重新完整的写一遍，哪怕是iPython这种交互式的shell，也并不会好到哪里去.

请从jupyter notebook开始 
>jupyter 还有一个jupytelab 的项目正在进行中，可能大家读到的时候已经可以完全正常的使用了

jupyter的notebook 文件是.ipnb 文件
是一个文本文件，它能够在jpyter中渲染出网页，在页面中交互式的执行代码，书写注释，笔记（甚至在笔记中引用代码中的变量）
也能方便的将你的执行结果或者执行源代码share 给_其他人, 所以jupyter notebook
是python 学习的最佳入门平台.

为什么不使用IDE 开始呢？
pycharm是很好的IDE， 但是开始工程性开发之前，并不需要用到它.
它的虚拟环境设置等project scope的配置也会让你转移注意力偏移目标,
对练习并不方便.   即使将来进入工程性开发，jupyter notebook
对于你的个人修炼，仍然必不可少，这是两个方向上应用的不同工具，并不能互相替代.


