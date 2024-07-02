# typora使用方法

## Windows版本安装

[下载地址](https://typora.io/#download)

激活（破解）办法：

```

安装完成后先启动一次Typora，看到激活提示，不需要点试用，直接关闭软件即可。

接着找到安装路径，因为我是单用户安装，所以在是在AppData目录下的，如果是全用户安装，就是在 C:\Program Files

<Typora安装路径>\Typora\resources\page-dist\static\js
例子：

C:\Users\<用户名>\AppData\Local\Programs\Typora\resources\page-dist\static\js
修改文件
在目录下找到 LicenseIndex 开头的 Js文件：Windows 里有两个


打开文件编辑，建议在编辑前先拷贝一份原文件作为备份

本次使用VScode作为演示编辑工具，Ctrl + H 进行替换：

# 搜索
hasActivated="true"==e.hasActivated
# 替换
hasActivated="true"=="true"
```
