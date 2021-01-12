---
title: 创建python虚拟环境
date: 2021-01-11
weight: 1
description: 创建python虚拟环境
categories:
- 项目
tags:
- Python
- 虚拟环境
---
创建*虚拟环境*使我们可以在虚拟环境中安装某个项目所需要的各种包，并与其他python包相互独立，避免多个项目所需的包互相冲突，而且在部署时可以快速的导出项目所需要的包的列表。
## 创建虚拟环境
对于高版本的Python，我们可以直接使用如下名了创建虚拟环境：
```
C:\Users\xiaoxi\Desktop>python -m venv sxb_env
```

## 激活虚拟环境
创建完成后，即可使用下面的命令激活虚拟环境：
```
C:\Users\xiaoxi\Desktop>cd sxb_env
C:\Users\xiaoxi\Desktop\sxb_env>
C:\Users\xiaoxi\Desktop\sxb_env>Scripts\activate

(sxb_env) C:\Users\xiaoxi\Desktop\sxb_env>
```
当看见环境名`sxb_env`包含在括号中时，就说明虚拟环境已经成功激活。


需要关闭虚拟环境时，只需执行：
```
(sxb_env) D:\Study\sxb_env\Scripts>deactivate
```

现在已经成功创建了虚拟环境，并掌握了激活和退出虚拟环境的命令，接下来就进一步创建Django应用了。