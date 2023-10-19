# Docker_Kafka

## 环境配置（依赖和工具）

1.git

    # 安装
    yum install git

    #验证
    [root@localhost ~]# git --version

2.查看服务器时区（这是个巨坑,一定要设置！设置！设置！）

    a.查看时区  date  或   hwclock
    b.列出时区  timedatectl list-timezones
    c.设置时区  timedatectl set-timezone Asia/Shanghai
    d.查看是否修改成功  date
    e.Centos8安装时间同步服务

    下面安装方式二选一进行安装即可：
    dnf install -y chrony
    yum install -y chrony

    更好的方式是让chronyd后台运行，自动同步时间：
    systemctl enable chronyd
    systemctl start chronyd

3.安装 Screen 服务（可用于 SSH 断开离线下载等会话操作）

    yum  install screen              #安装

    screen -S  tron-back             #创建screen会话(tron-back为会话名称)

    screen -ls                       #查看所有screen会话

    按键盘上面的Ctrl+a，然后再按d      #保存当前的screen会话

    exit   #退出screen

    screen -wipe  tron-back          #删除会话

4.Telnet 命令

    # AlmaLinux / Rocky Linux / CentOS / Fedora
    # sudo yum -y install telnet

    # Ubuntu / Debian
    # apt-get install telnet

5.在 Amazon Linux 2 上安装 docker-compose 的步骤如下

    1>使用以下命令从 GitHub 的 docker/compose 仓库下载并安装最新版的 docker-compose

        sudo curl -L "https://github.com/docker/compose/releases/download/latest/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

    2>为 docker-compose 命令设置执行权限

        sudo chmod +x /usr/local/bin/docker-compose

    3>执行以下命令验证 docker-compose 的版本

        docker-compose --version

## Docker环境下部署Zookeeper & Kafka(当前版本Kafa的还有一些需要与Zookeeper联合运行)

    1.Win环境下运行部署

        1>. 进去文件夹< Kafka-Cluster-Win >
        2>. 运行命令  docker-compose up -d
