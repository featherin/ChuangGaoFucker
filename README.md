# ChuangGaoFucker

### 死亡一周年纪念💊💊💊

检讨：
1. 本来可以用现代js语法再babel的 -> [甚至可以上ts](https://github.com/winderica/GoodbyeRE)
2. 路径几乎是写死的，数据点太少了，等等 -> 然而他们的检测也很简单，更多的是人的问题
3. 🔥🔥🔥🔥某人🔥🔥🔥🔥二次封装成apk，降低门槛，都是他的错！！！😤😤😤 -> 闷声发大财，这是坠吼滴

### How To Use

0. clone本仓库
1. 确保你的手机已经root，并已开启adb调试
2. 下载[Android Platform Tools](https://developer.android.com/studio/releases/platform-tools)，并解压
3. 确保已经安装`Python3`
4. 安装frida
    ```sh
    $ pip install frida
    ```
5. 下载对应架构的[frida-server](https://github.com/frida/frida/releases)，并解压
6. 连接手机，将frida-server运行在手机上
    ```sh
    $ cd platform-tools/ # 自行替换路径，不再赘述
    $ ./adb root
    $ ./adb push frida-server /data/local/tmp/
    $ ./adb shell "chmod 755 /data/local/tmp/frida-server"
    $ ./adb shell "/data/local/tmp/frida-server &"
    ```
    以后每次运行只需输入如下命令
    ```sh
    $ ./adb root
    $ ./adb shell "/data/local/tmp/frida-server &"
    ```
7. 为确保frida-server已经运行，输入
    ```sh
    $ frida-ps -U
    ```
    此时将输出进程列表。
8. 输入
    ```sh
    $ frida -l hooks.js -U -f net.crigh.cgsport --no-pause
    ```
    此时应用开启，进入开始跑步后直接结束即可完成。
    
    数据是随机且精心设计的，除了路线，有需要可自行更改`beganPoint`、`endPoint`、`points`，之后会加入更改路线的功能。
    
    若有报错的情况，请在`hook.js`中注释掉[第407行](https://github.com/winderica/ChuangGaoFucker/blob/294129a30a39b1c3630580f7a521b5c92e1b06e7/hooks.js#L407)；同时可能会伴随着重启，请享受这个过程。
    
    仍然没法执行，或数据无法上传，请提issue。

### Notifications

* 目前由于没有hook setter，应用内的数据会与上传的数据不同。清除应用的数据、缓存后重新打开即可正常显示。详见[这个issue](https://github.com/winderica/ChuangGaoFucker/issues/3#issuecomment-470395474)
* 想要改`hook.js`，请注意frida不支持ES6及其以上的特性

### TODO

* 更改setter -> 可惜没做完
* 用户自定义路线 ->可惜没做完
* 原理 -> 写了也没用
* 通过`frida-gadget`实现免root -> 这是不可能的
