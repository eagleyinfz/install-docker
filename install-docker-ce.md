# install docker-ce

## 在线安装
卸载旧版本，使用yum源
```shell
$ sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
$ sudo yum install -y yum-utils device-mapper-persistent-data lvm2

```
国内源
```shell
 sudo yum-config-manager \
    --add-repo \
    https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```
官方源
```shell
$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```
如果需要最新版本的 Docker CE 请使用以下命令：
```shell
$ sudo yum-config-manager --enable docker-ce-edge
$ sudo yum-config-manager --enable docker-ce-test
```
更新 yum 软件源缓存，并安装 docker-ce
```shell
$ sudo yum makecache fast
```
查询docker-ce版本
```shell
$ yum list docker-ce --showduplicates | sort -r
* updates: mirrors.aliyun.com
Loading mirror speeds from cached hostfile
Loaded plugins: fastestmirror
Installed Packages
 * extras: mirrors.aliyun.com
docker-ce.x86_64            3:18.09.6-3.el7                    docker-ce-stable 
docker-ce.x86_64            3:18.09.5-3.el7                    docker-ce-stable 
docker-ce.x86_64            3:18.09.4-3.el7                    docker-ce-stable 
docker-ce.x86_64            3:18.09.3-3.el7                    docker-ce-stable 
docker-ce.x86_64            3:18.09.2-3.el7                    docker-ce-stable 
docker-ce.x86_64            3:18.09.1-3.el7                    docker-ce-stable 
docker-ce.x86_64            3:18.09.0-3.el7                    docker-ce-stable 
docker-ce.x86_64            18.06.3.ce-3.el7                   docker-ce-stable 
docker-ce.x86_64            18.06.3.ce-3.el7                   @docker-ce-stable
docker-ce.x86_64            18.06.2.ce-3.el7                   docker-ce-stable 
docker-ce.x86_64            18.06.1.ce-3.el7                   docker-ce-stable 
docker-ce.x86_64            18.06.0.ce-3.el7                   docker-ce-stable 
docker-ce.x86_64            18.03.1.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            18.03.0.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.12.1.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.12.0.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.09.1.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.09.0.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.06.2.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.06.1.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.06.0.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.03.3.ce-1.el7                   docker-ce-stable 
docker-ce.x86_64            17.03.2.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.03.1.ce-1.el7.centos            docker-ce-stable 
docker-ce.x86_64            17.03.0.ce-1.el7.centos            docker-ce-stable 
```
安装指定版本18.06.3
```shell
$ yum install -y  docker-ce-18.06.3.ce-3.el7.x86_64
```
安装指定版本18.09.7-3
```shell
$ yum install -y  docker-ce-18.09.7-3.el7.x86_64
```
更新docker配置
```shell
$ vi /etc/docker/daemon.json
{
    "registry-mirrors": ["http://hub-mirror.c.163.com"],
	"insecure-registries":["192.168.1.239:5000"],
	"log-opts":{
		"max-size": "500m",
  		"max-file": "5"
	}
}
```
启动
```shell
$ systemctl daemon-reload && systemctl enable docker && systemctl start docker
```
## 离线安装
在线下载指定版本
```shell
$ wget https://download.docker.com/linux/centos/7/x86_64/stable/Packages/docker-ce-cli-18.09.7-3.el7.x86_64.rpm
$ wget https://download.docker.com/linux/centos/7/x86_64/stable/Packages/docker-ce-18.09.7-3.el7.x86_64.rpm
```

离线安装
```shell
yum localinstall -y *.rpm
```