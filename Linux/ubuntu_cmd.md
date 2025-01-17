# ubuntu设置root密码
```sudo passwd root
```
# 查看Ubuntu版本
```
cat /etc/issue
```
# 更新
```
apt-get update
apt-get install vim
```
**容器内查看Linux版本号**
```
cat /etc/issue
```
# 更换/etc/apt/sources.list文件里的源
```
sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list 
```
## 备份源列表
## 首先备份源列表
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
```
# 打开sources.list文件
```
vim /etc/apt/sources.list
```
**编辑/etc/apt/sources.list文件, 在文件最前面添加阿里云镜像源：**
```vim
#阿里源
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
```

# 网络工具
```
sudo apt install net-tools
```

# 安装驱动管理
```
apt install ubuntu-drivers-common
```

# 显卡驱动
## 查看版本
```
ubuntu-drivers devices
```
## 安装推荐版本
```
sudo ubuntu-drivers autoinstall
```
## 安装指定版本
```
sudo apt install nvidia-470
```


# 安装常用软件包
```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
# git
apt-get install git
```

# 代理
## 设置代理
```bash
export http_proxy=http://127.0.0.1:12333
export https_proxy=http://127.0.0.1:12333
curl www.google.com
```
## 检查代理
```bash
echo $http_proxy 
echo $https_proxy 
env|grep -i proxy
```
## 取消代理
```bash
unset http_proxy
unset https_proxy
unset no_proxy
unset all_proxy
export http_proxy=""
export https_proxy=""
export HTTP_PROXY=""
export HTTPS_PROXY=""
export ALL_PROXY=""
```

## 设置git代理
```bash
git config --global http.proxy http://127.0.0.1:12333
git config --global https.proxy https://127.0.0.1:12333
```

## 取消git代理
```bash
git config --global --unset http.proxy
git config --global --unset https.proxy
```


# 安装jdk8
```bash
sudo apt install openjdk-8-jdk
切换java命令软连接指向
sudo update-alternatives --config java 
```
# 查询当前目录空间使用情况
du --max-depth=1 -h 

# docker
## 安装
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
sudo apt-get update
## 状态
service docker status
## 启动
sudo service docker start
## 停止
sudo service docker stop
## 重启
sudo service docker restart

## 卸载
sudo apt-get remove docker docker-engine docker.io containerd runc
### 查询相关软件包
dpkg -l | grep docker
### 删除这个包
sudo apt remove --purge docker.io
