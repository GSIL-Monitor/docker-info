# jupyterhub 搭建文档

此文档为jupyterhub搭建文档，描述搭建jupyterhub环境。  

## 服务器环境

centos7 4core 8g内存

## root用户,创建jupyterhub用户并配置sudo

useradd jupyterhub  
passwd jupyterhub

visudo 添加jupyter的sudo配置

jupyter ALL=(ALL)       ALL

## jupyterhub用户,使用jupyterhub用户安装jupyter相关组件

切换到jupyterhub用户

su - jupyterhub

## jupyterhub用户,安装conda

在conda官网[https://www.anaconda.com/]上选择conda版本,可以选择最小版本，也可以选择完整版，这里选择完整版本。  

下载  
wget https://repo.anaconda.com/archive/Anaconda3-5.3.1-Windows-x86_64.exe

安装bzip2否则安装anaconda会报  
bunzip2: command not found  
yum install -y bzip2

使用sh安装conda  
sh Anaconda3-5.3.1-Linux-x86_64.sh

一路选择yes,后面有询问是不是要安装微软的一些包选yes,询问sudo的密码填写密码继续安装。

## jupyterhub用户,使用conda安装jupterhub软件

conda install -c conda-forge jupyterhub  

## jupyterhub用户,使用conda安装jupyterNotebook

conda install notebook

## jupyterhub用户,创建运行目录并生成jupyterhub的配置文件
创建目录  
mkdir ./app  
进入目录    
cd ./app  
创建jupyterhub的配置文件，会生成一个jupyterhub_config.py的配置文件  
jupyterhub --generate-config  
修改这个配置文件的c.JupyterHub.bind_url(如果有需要)  
c.JupyterHub.bind_url = 'http://:8000/jupyter'

## root用户,配置sudo的环境变量
visudo  
Defaults    secure_path = /sbin:/bin:/usr/sbin:/usr/bin:/home/jupyter/anaconda3/bin

## root用户,修改jupyerhub用户文件夹的权限755
chmod 755 /home/jupyterhub

## jupyter用户,启动jupyterhub
如果需要支持多用户，请用sudo启动  
sudo jupyterhub -f /home/jupyter/app/jupyterhub_config.py --no-ssl  
nohup sudo先要用sudo命令输入密码,比方说sudo vi  
nohup sudo jupyterhub -f /home/jupyter/app/jupyterhub_config.py --no-ssl > jupyterhub.log &  
jupyterhub已经启动在bind_url上,可以用jupyter用户和密码登陆.

## root用户,添加jupyterhub的其他用户
添加用户user1指定用户组为jupyter  
useradd user1 -g jupyter  
passwd user1 *****  
设置user1的目录权限为755  
chmod 755 /home/user1  
至此可以用user1/xxxx登陆jupyterhub

## jupyterhub用户,jupyterhub添加依赖包
可以在jupyterhub用户的conda添加依赖包  
语法为conda install elasticsearch
conda install elastic
conda install theano  
conda install keras  
pip install xgboost  
conda install pyspark  
conda install impyla  
conda install pycurl  
conda install -c conda-forge fbprophet
