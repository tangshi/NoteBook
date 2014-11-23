# Mac命令行备忘录


1.使用`caffeinate`阻止Mac运行屏幕保护和睡眠

`caffeinate`能阻止Mac进入睡眠状态，而且屏幕保护也不会激活。我们最好使用-t为命令加入具体的时间。比如下面的命令可以使Mac一小时内不进入睡眠状态。

    caffeinate -t 3600



2.使用`pkgutil`解压PKG文件

如果你想查看PKG安装文件中的某个特殊文件，你可以使用`pkgutil`命令完成。下面的命令会将macx.pkg文件解压至桌面的macx文件夹下，该文件夹不可以是已存在的文件夹，建议命名为与pkg文件同名。

    pkgutil --expand macx.pkg ~/Desktop/macx

解压pkg文件以后，你可能想对pkg里的文件稍作改动，如果改动一些脚本文件里的命令等，这是允许的。改动完成后，使用以下命令将当前目录下的`macx`文件夹的内容重新生成`macx.pkg`安装包。

    pkgutil --flatten ./macx/ macx.pkg



3.使用`purge`命令释放内存

`purge`命令可以清除内存和硬盘的缓存，与重启Mac的效果差不多。`purge`命令可以让不活跃的系统内存转变为可以使用的内存。你只需在终端中输入下面的命令即可。

    purge


4.使用`open`命令开启多个相同应用

`open`命令可以在终端中开启应用，使用`-n`可以开启多个相同应用。比如你可以使用下面的命令开启新Safari窗口

    open -n /Applications/Safari.app/


5.不通过App Store更新OS X

想要更新系统却不想打开臃肿的Mac App Store？下面的命令可以帮助你使用终端升级OS X。

    sudo softwareupdate -i -a


6.将所有下载过的文件列出来

我们可以通过下面的命令将所有下载过的内容列出来


    sqlite3 ~/Library/Preferences/com.apple.LaunchServices.QuarantineEventsV* 'select LSQuarantineDataURLString from LSQuarantineEvent' |more


7.使用`chflags`命令隐藏文件或文件夹

如果你想让某个文件或文件夹影藏，那么`chflags`命令可以实现。你只需将文件路径填对即可，比如我们向隐藏桌面上的macx文件夹。如果你想再次看到文件夹，只需将`hidden`改为`nohidden`即可。

    chflags hidden ~/Desktop/macx

显示Mac隐藏文件的命令：

    defaults write com.apple.finder AppleShowAllFiles -bool true 

隐藏Mac隐藏文件的命令：

    defaults write com.apple.finder AppleShowAllFiles -bool false


9.创建有密码保护的压缩文件

你可以通过下面的命令将桌面上的macx.txt文件创建成有密码保护压缩文件protected.zip。

    zip -e protected.zip ~/Desktop/macx.txt

10.定时关机/重启/睡眠

设定2012年9月3日23:15分关机：`sudo shutdown -h 1209032315`    
设定2012年9月3日23:15分重启：`sudo shutdown -r 1209032315`    
设定2012年9月3日23:15分睡眠：`sudo shutdown -s 1209032315`    

命令的主体主要是 `Shutdown，h/r/s` 分别代表关机/重启/睡眠，然后在后面加上执行时间(`yymmddhhmm`)即可。
 
如果想临时取消定时关机/睡眠/重启,我们在终端中执行了2012年9月3日23:15分关机的命令，终端中会显示如下：
 
> mbp:~ $ sudo shutdown -h 1209032315
> Shutdown at Mon Sep 3 23:15:00 2012.
> shutdown: [pid 577]

注意上面的 `pid 577`，这是指当前运行的这个`shutdown`命令的进程号，如果要取消关机，只需要停止这个进程的运行就可以了。命令为： 

    sudo kill 577


11.App Store开启Debug窗口

    defaults write com.apple.appstore ShowDebugMenu -bool true


12.元数据相关命令

`mdfind` 根据匹配规则查找文件    
`mdls`   列出指定文件的元数据    
`mdutil` 管理元数据    
