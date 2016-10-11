由于公司网络的限制，`pip`没办法下载和安装依赖库，查资料后发现可以通过使用国内镜像源或使用代理的方式解决这个问题，记录如下，以备不时之需。

首先检测配置文件是否存在，没有则创建之。配置文件的路径（本用户有效）：

- Unix:`$HOME/.config/pip/pip.conf`
- Mac: `$HOME/Library/Application Support/pip/pip.conf`
- Windows：`%APPDATA%\pip\pip.ini`，`%APPDATA%`的实际路径我电脑上是`C:\Users\user_xxx\AppData\Roaming`，可在cmd里执行`echo %APPDATA%`命令查看

`virtualenv`和全局的配置文件路径参见[pip文档](https://pip.pypa.io/en/stable/user_guide/#config-file)

配置文件内容如下：

```
[global]
index-url = http://mirrors.aliyun.com/pypi/simple/ # 这里使用的是阿里云的镜像源
proxy=http://xxx.xxx.xxx.xxx:8080 # 替换出自己的代理地址，格式为[user:passwd@]proxy.server:port

[install]
trusted-host=mirrors.aliyun.com # 信任阿里云的镜像源，否则会有警告
```

配置文件的原则就是，凡是`pip`命令行的参数都可以在配置文件里定义其默认值！   
至于`[global]`、`[install]`等标志用于声明配置项的作用域，`[global]`下的配置项全局有效，而`[install]`下的配置项只在使用`pip install`命令时有效。
