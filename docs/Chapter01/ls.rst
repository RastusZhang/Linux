ls 显示目录内容
##########################

ls 命令（list）用来显示目标列表，在 Linux 中是使用率较高的命令。

根据 Eric Fischer 在 Linux 文档项目中关于 ls 命令的文章，该命令的起源可以追溯到 1961 年 MIT 的相容分时系统上的 listf 命令。根据维基百科，ls 出现在 AT&T Unix 的原始版本中。我们今天在 Linux 系统上使用的 ls 命令来自 GNU Core Utilities。还有一种是 BSD 版本，安装在部分 BSD 或 MacOS 操作系统。

命令格式：
***********************

.. highlight:: none

::

    ls [OPTION]... [FILE]...

常用选项：
***********************

::

    -a, --all
      显示所有的文件，包括隐藏文件（以 ``.`` 开头的文件）

    -A, --almost-all
      显示所有的文件，包括隐藏文件，但不包括表示当前目录 . 和上级目录 .. 这两个文件

    -C
      多列显示输出结果。这是默认选项

    --color[=WHEN]
      是否根据文件类型显示颜色，WHEN 可以为 never、always 或者 auto

    -F
      在每个输出项后追加文件的类型标识符
      具体含义：“*”表示具有可执行权限的普通文件
              “/”表示目录
              “@”表示符号链接
              “|”表示命令管道 FIFO
              “=”表示 sockets 套接字
              当文件为普通文件时，不输出任何标识符

    -i, --inode
      列出文件的索引节点号（inode）

    -l
      以长格式显示目录下的内容列表。
      输出的信息从左到右依次包括：文件类型、权限模式、硬连接数、所有者、组、文件大小、最后修改时间、文件名

    -m
      用逗号 ``,`` 区隔每个文件和目录的名称

    -R
      递归处理，将指定目录下的所有文件及子目录一并处理

    -t
      根据文件和目录的更改时间进行排序输出（最新的文件先列出）

使用实例：
***********************

1. 显示长格式列表

::

    [root@localhost /]# ls -l
    total 20
    lrwxrwxrwx.   1 root root    7 Mar 27  2018 bin -> usr/bin
    dr-xr-xr-x.   5 root root 4096 Mar 27  2018 boot
    ...
    drwxr-xr-x.  20 root root  278 Feb 12 18:17 var

2. 将文件大小转换为更加人性化的表示方法（默认的以字节为单位）

::

    [root@Document /]# ls -h
    -rwxrwx---. 1 seth users    455 Mar  2  2017 estimate.sh
    -rwxrwxr-x. 1 seth seth     662 Apr 29 22:27 factorial
    -rwxrwx---. 1 seth users    20M Jun 29  2018 fop-2.3-bin.tar.gz
    -rwxrwxr-x. 1 seth seth    6.1K May 22 10:22 geteltorito
    -rwxrwx---. 1 seth users    177 Nov 12  2018 html4mutt.sh

3. 显示所有的文件，包括隐藏文件

::

    [root@localhost ~]# ls -a
    .   .bash_history  .bash_profile  .cshrc          .pki
    ..  .bash_logout   .bashrc        .mysql_history  .tcshrc

4. 显示长格式列表并且显示文件的索引节点号

::

    [root@localhost /]# ls -li
    total 20
          120 lrwxrwxrwx.   1 root root    7 Mar 27  2018 bin -> usr/bin
           64 dr-xr-xr-x.   5 root root 4096 Mar 27  2018 boot
    ...
    100663361 drwxr-xr-x.  20 root root  278 Feb 12 18:17 var

5. 在每个输出项后追加文件的类型标识符

::

    [root@localhost /]# ls -F
    bin@   dev/  home/  lib64@  mnt/  proc/  run/   srv/  tmp/  var/
    boot/  etc/  lib@   media/  opt/  root/  sbin@  sys/  usr/

6. 显示目录下所有的 php 文件

::

    [root@localhost owncloud]# ls -l *.php
    -rwxrwxrwx 1 root root 4371 Feb 12 19:38 console.php
    -rwxrwxrwx 1 root root 5033 Feb 12 19:38 cron.php
    -rwxrwxrwx 1 root root 3678 Feb 12 19:38 index.php

7. 递归显示目录下文件

::

    [root@localhost updater]# ls -FR
    .:
    app/              COPYING-AGPL*  pub/        src/
    application.php*  index.php*     README.md*  vendor/

    ./app:
    bootstrap.php*  config/

    ./app/config:
    container.php*

    ./pub:
    css/  img/  js/

    ./pub/css:
    main.css*

8. 只显示目录下的文件夹

::

    [root@localhost updater]# ls -la | grep ^d
    drwxr-xr-x 21 root  root  4096 Jul 13 13:49 .
    drwxr-xr-x  3 root  root   4096 Jul  8 22:54 ..
    drwxr-xr-x  2 root  root  4096 Jul  9 14:59 Desktop
    drwxr-xr-x  8 root  root  4096 Jul 13 18:30 Documents
    drwxr-xr-x  2 root  root 12288 Jul 13 15:49 Downloads
    drwxr-xr-x  2 root  root  4096 Jul  9 14:59 Music
    drwx------  2 root  root  4096 Jul 10 09:51 .ssh
    drwxr-xr-x  2 root  root  4096 Jul  9 14:59 Templates
    drwxr-xr-x  7 root  root  4096 Jul 11 11:43 Videos

