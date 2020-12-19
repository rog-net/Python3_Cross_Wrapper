<h1 align="center">
  Python3 Cross Wrapper
</h1>

<p align="center">
  <img src="https://img.shields.io/badge/build-passing-brightgreen.svg?style=flat"/>
  <img src="https://img.shields.io/github/license/rog-net/Python3_Cross_Wrapper.svg?style=flat"/>
</p> 

Python3交叉封装器，在x86_64架构的GNU/Linux下利用Docker与Vagrant，模拟不同操作系统和异指令集架构操作系统，对python3脚本使用pyinstaller封装对应的二进制可执行文件  
### 目前支持  
Linux : ``arm64, armel, armhf, amd64, i386, mips64ls, ppc64le, s390x``  
FreeBSD : `<准备上线>`  
生成后二进制文件运行环境GLIBC版本需在2.24以上

## 开始
建议全程在Debian10 amd64下操作系统操作
### 运行`firsh.sh`一键安装Vagrant Docker Virtualbox等软件，也可以自行安装  
`chmod +x firsh.sh`  
`./firsh.sh`  

### 安装 qemu-static-user
`docker run --rm --privileged multiarch/qemu-user-static --reset -p yes`

### 开始构建镜像
`chmod +x ./build.sh`  
`./build.sh`  
可以运行`./list.sh`和`cat build_out/linux-<指令集架构>.out`检测进度  
构建和封装分别用时30分钟到1小时不等

### 封装python3脚本
在source_code下导入项目文件夹，默认为example，第一个运行参数为项目名称，第二个为项目路径  
`./run.sh example_test source_code/example/`  
可以运行`./list.sh`和`cat run_out/linux-<指令集架构>.out`检测进度  

### 封装结束后，所有可执行文件均在output_bin下以zip压缩文件包的形式出现，需解压后运行
