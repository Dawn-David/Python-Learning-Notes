# 关于Anaconda
我安装了anaconda，

        Anaconda是一个方便的python包管理和环境管理软件，一般用来配置不同的项目环境。
       
 [入门介绍连接](https://www.jianshu.com/p/742dc4d8f4c5)<br>
 [Anaconda快速使用教程](https://www.jianshu.com/p/20a92e5eb9af)<br>
 [Anaconda完全入门指南](https://www.jianshu.com/p/eaee1fadc1e9)<br>

# conda命令
当要安装第三方库或者更新时，需在Anaconda Prompt命令行里面输入命令：

        conda list 列举当前环境下的所有包
        conda list -n packagename 列举某个特定名称包
        conda install packagename 为当前环境安装某包
        conda install -n envname packagename 为某环境安装某包
        conda search packagename 搜索某包
        conda updata packagename 更新当前环境某包
        conda update -n envname packagename 更新某特定环境某包
        conda remove packagename 删除当前环境某包
        conda remove -n envname packagename 删除某环境环境某包
                
 # 清华源安装
 安装时，常因软件过大，网络连接差，导致安装失败，因此才有清华源安装<br>
 写入默认的安装地址的命令如下：
        
        conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
        conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
        conda config --set show_channel_urls yes
  
特别注意：因删除倒数第二行的-default，以免造成错误。<>
设置好的.condarc文件如下：

        channels:
                - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
                - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
                - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
        show_channel_urls: true

# Anaconda环境
Anaconda的基础环境，路径为：C:\ProgramData\Anaconda3，包安装路径在：\Lib\site-packages
Anaconda的新建环境，路径为：C:\Users\dell\.conda，包安装路径同上

        基础环境路径：C:\ProgramData\Anaconda3
        新建环境路径：C:\Users\dell\.conda\envs\tensorflow
        
        激活环境：activate 环境名称
        退出环境：conda deactivate
 
# Pytorch安装
[pytorch快速安装【清华源】](https://blog.csdn.net/zzq060143/article/details/88042075)<br>
[Windows环境下Anaconda3安装配置pytorch详细步骤（踩坑汇总）](https://blog.csdn.net/qq_41282258/article/details/98961667)<br>

# TensorFlow版本
[选择安装的TensorFlow版本](https://blog.csdn.net/qiancaobaicheng/article/details/95226499)<br>
然后使用conda命令，安装选择的TensorFlow版本

        
        查询：conda search tensorflow
        安装：conda install tensorflow=2.0

