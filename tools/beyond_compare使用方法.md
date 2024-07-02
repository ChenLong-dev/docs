# beyond compare 使用方法

破解原理就是删掉BC4 用来记录试用天数的cache，让自己一直保持试用。

新建一个.txt，输入以下神秘代码，并保存成refreshBeyondCompare.bat。

reg delete "HKEY_CURRENT_USER\Software\Scooter Software\Beyond Compare 4" /v CacheID /f

运行 refreshBeyondCompare.bat 文件

此时运行即可重置试用时间。

然后为了让机器自动去重置，我们在把他放到开机启动程序里：

C:\Users\Administrator\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

好了，此时，开机就会自动刷新BC4的试用时间，可以让我们一直保持试用状态。
