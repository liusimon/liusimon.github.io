Win10 wsl 子系统ssh服务自启动设置, 步骤如下：  
  
    Linux版本：Ubuntu 18.04

创建并编辑 /etc/init.wsl

    sudo nano /etc/init.wsl

加入如下内容：

    #! /bin/sh
    /etc/init.d/ssh $1

添加执行权限:

    sudo chmod +x /etc/init.wsl

添加文件/etc/sudoers.d/nopasswd，避免输入密码：

    sudo nano /etc/sudoers.d/nopasswd

加入如下内容：

    %sudo ALL=NOPASSWD: /etc/init.wsl

在 Windows 启动或者登陆的时候执行该脚本, 在 Windows 中，开始-运行里面输入shell:startup打开启动文件夹，创建文件startservice.vbs，脚本内容：

    Set ws = CreateObject("Wscript.Shell")
    ws.run "ubuntu1804 run sudo /etc/init.wsl start", vbhide

如果你用的不是 ubuntu18.04 的发行版，那么修改上面脚本里面的ubuntu1804为你用的发行版运行命令，如：debian 
