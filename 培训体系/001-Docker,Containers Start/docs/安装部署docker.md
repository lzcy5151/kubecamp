# docker 安装实验手册

CentOS：

```bash
    #清理系统原有版本

    systemctl stop firewalld
    systemctl disable firewalld

    setenforce 0

    #修改selinux的配置文件

    yum remove docker \
            docker-client \
            docker-client-latest \
            docker-common \
            docker-latest \
            docker-latest-logrotate \
            docker-logrotate \
            docker-engine

    #安装yum管理工具
    yum install -y yum-utils    

    #添加yum仓库
    yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo


    #安装docker引擎
    yum install docker-ce docker-ce-cli containerd.io

    #查看docker引擎可用版本
    yum list docker-ce --showduplicates | sort -r

    #启动docker
    systemctl start docker

    #自启动docker
    systemctl enable docker
```

Ubuntu：

```bash
    #卸载过往版本
    sudo apt-get remove docker docker-engine docker.io containerd runc

    sudo apt-get update

    sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg-agent \
        software-properties-common

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

    sudo apt-key fingerprint 0EBFCD88

    sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) \
    stable"

    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io
```
