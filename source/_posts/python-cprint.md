---
title: Python使用cprint模块打印带颜色字符
---

在终端打印带有颜色的字符串

安装
``` bash
pip install cprint
```
使用示例：
``` python
from cprint import *

cprint(str) # WHITE
cprint.ok(str) # BLUE
cprint.info(str) # GREEN
cprint.warn(str) # YELLOW
cprint.err(str, interrupt=False) # BROWN
cprint.fatal(str, interrupt=False) # RED
```