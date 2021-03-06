alias 命令别名
####################################

alias 命令用于查看和创建命令别名，别名允许用户只输入一个单词就运行任意一个命令或一组命令。


命令格式：
************************************

.. highlight:: none

::

    alias [name] = [command ...]
 

举个例子，为常用的 clear（清除屏幕）命令创建一个别名 c：

::

    [Linux]$ alias c = 'clear'



让别名永久生效
************************************

在设置别名后，只在当前登录会话中有效。如果你登出或重启系统后，别名就会消失了。你可以将别名定义写入配置文件 ``~/.bashrc`` 中，输入：

::

    [Linux]$ vi ~/.bashrc

    # 添加下面内容让别名永久有效：
    alias c = 'clear'

保存并关闭文件就行了。系统级的别名（也就是对所有用户都生效的别名）可以放在 ``/etc/bashrc`` 文件中。请注意，``alias`` 命令内建于各种 shell 中，包括 ksh，tcsh/csh，ash，bash 以及其他 shell。



.. hint ::

    以下的方法可以临时性地禁用命令别名：

    ::

        # 在命令前边加入转义符：
        [Linux]$ \ls
        
        # 使用命令的绝对路径：
        [Linux]$ /usr/bin/ls
        
        # 或者对命令加上引用：
        [Linux]$ "ls"
        [Linux]$ 'ls'
        
        # 使用 command 命令
        [Linux]$ command ls


系统中常用的别名
************************************

::

    # 使用颜色输出 ls 的内容，许多发行版默认设置
    alias ls = 'ls --color=auto'

    # 使用颜色输出 grep 查找到的内容
    alias grep = 'grep --color=auto'
    alias egrep = 'egrep --color=auto'
    alias fgrep = 'fgrep --color=auto'


    # 对其输出 mount 的内容
    alias mount = 'mount | column -t'

    # 默认添加 ping 的次数
    alias ping = 'ping -c 5'

    # 删除文件时需要确认
    alias rm = 'rm -i'

    # 更新 Debian 系统中的软件
    alias update = 'sudo apt-get update && sudo apt-get upgrade'

    # wget 默认断点续传
    alias wget = 'wget -c'

