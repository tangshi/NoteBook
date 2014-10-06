# Cocos2d-x 打包安卓apk安装包

#### 1. 下载`Android SDK`

#### 2. 下载`Android NDK`

注意点：

1. `cocos2dx 3.2`以前，只支持r9版本的ndk，官网最新版是r10，升级`cocos2dx`是不错的选择，当然也可以下载r9版本的ndk
2. NDK分多个版本，我开始选择`Platform
(64-bit target) Mac OS X 64-bit`版本，发现`cocos2dx`不支持，所以下载了`Platform
(32-bit target) Mac OS X 64-bit`版本，支持

#### 3. 安装`ant`

一般安卓的IDE会集成`ant`，但是我只下载sdk，没有下载`eclipse`之类的IDE(我不需要)，所以直接用`Homebrew`安装了`ant`

#### 4. 配置`cocos2dx`的安卓环境

终端进入`cocos2dx sdk`根目录，执行`setup.py`脚本，期间会要求输入`Android SDK`、`Android NDK`和`ant`的根目录，注意输入根路径时开头和结尾都不能有多余的空格，按照提示设置`Android SDK`和`Android NDK`的根路径即可，`ant`由于是用`Homebrew`安装的，环境变量已经配置好了，脚本会自己找到的，不需要手动输入根路径。

#### 5. 打包apk

终端进入待打包的项目的根目录，执行 `cocos run -p android`编译项目(当然这是使用安卓平台下默认的编译命令)，编译结束后安装包生成在 `./bin/debug/android/`目录下。

关于`cocos run`命令的具体使用，可以`cocos run -h`查看帮助：

```
usage: cocos run [-h] [-s SRC_DIR] [-q] [-p PLATFORM] [-m MODE] [-b BROWSER]
                 [--host [SERVER_HOST]]
                 [SERVER_PORT]

Compiles & deploy project and then runs it on the target

optional arguments:
  -h, --help            show this help message and exit
  -s SRC_DIR, --src SRC_DIR
                        project base directory
  -q, --quiet           less output
  -p PLATFORM, --platform PLATFORM
                        select a platform (android, ios, mac, web, win32,
                        linux)
  -m MODE, --mode MODE  Set the run mode, should be debug|release, default is
                        debug.

web project arguments:
  -b BROWSER, --browser BROWSER
                        Specify the browser to open the url. Use the system
                        default browser if not specified.
  SERVER_PORT           Set the port of the local web server, defualt is 8000
  --host [SERVER_HOST]  Set the host of the local web server, defualt is 127.0.0.1
```