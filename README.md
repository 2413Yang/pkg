# pkg
some midware packages
# 1. 修改source.list
sudo gedit /etc/apt/sources.list
# 2. 添加ubuntu16的源
deb http://mirrors.aliyun.com/ubuntu/ xenial main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main

deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates universe

deb http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security universe

sudo apt-get update

# 如果发现update失败,提示NO_PUBKEY 40976EAF437D05B5，在命令行配置公钥
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5 3B4FE6ACC0B21F32

apt-cache policy gcc-5
## 命令行结果
gcc-5:
  Installed: 5.4.0-6ubuntu1~16.04.12
  Candidate: 5.4.0-6ubuntu1~16.04.12
  Version table:
 *** 5.4.0-6ubuntu1~16.04.12 500
        500 http://mirrors.aliyun.com/ubuntu xenial-updates/main amd64 Packages
        500 http://mirrors.aliyun.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.3.1-14ubuntu2 500
        500 http://mirrors.aliyun.com/ubuntu xenial/main amd64 Packages
##
sudo apt-get install gcc-5=5.4.0-6ubuntu1~16.04.12

# 查看安装有的gcc版本
ls /usr/bin/gcc*
# 如有多个gcc版本，则使用以下命令进行版本管理
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 40
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 50
sudo update-alternatives --config gcc

# g++安装： 与gcc同理
apt-cache policy g++-5
sudo apt-get install g++-5=5.4.0-6ubuntu1~16.04.12

# 安装9.*默认版本
sudo apt-get install gcc-9

# 相关依赖安装
sudo apt-get install build-essential
# 确认安装成功
gcc --version

# 安装gfortran, 指定版本
sudo apt-get install gfortran-5
