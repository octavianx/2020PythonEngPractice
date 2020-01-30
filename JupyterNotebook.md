
在jupyternotebook下导入自己写的模块，需要注意：
当更改自己的模块的内容后，要Restart内核，才能反映到使用该模块的.ipynb文件中。

但是实际上还有work around:  


具体的讨论可以参见:
[https://support.enthought.com/hc/en-us/articles/204469240-Jupyter-IPython-After-editing-a-module-changes-are-not-effective-without-kernel-restart|Jupyter / IPython: After editing a module, changes are not effective without kernel restart
 ]

TLDR:
直接的方法
https://ipython.readthedocs.io/en/stable/config/extensions/autoreload.html

在jupyter notebook中执行如下指令
```python
%load_ext autoreload
%autoreload 2
from foo import some_function

```
这个方法是有弊端的，它做不到的事情请参见原文中的caveats
> Replacing code objects does not always succeed: changing a @property in a class to an ordinary method or a method to a member variable can cause problems (but in old objects only).
> Functions that are removed (eg. via monkey-patching) from a module before it is reloaded are not upgraded.
> C extension modules cannot be reloaded, and so cannot be autoreloaded.

