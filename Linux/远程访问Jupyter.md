# 远程访问Jupyter Notebook

    相关配置:Ubuntu 16.04服务器,本地Win10，使用了Xshell，Xftp工具。
![Jupyter](https://i.loli.net/2020/03/02/yrBlXniYtmfSJkj.png)

相关配置主要分为三步：
- 服务器上的Jupyter配置
- 本地Xshell的配置
- 使用Jupyter Notebook

其中服务上的配置方法有两种：
- 使用命令行，`操作简单，登录稍繁`
- 使用配置文件，`操作略繁，登陆简单`

## 命令行配置服务器
- 首先要确保服务器上安装了Jupyter，如果未安装，安装命令如下：
```
pip install jupyter
```
- 命令行配置
    - 激活环境：`conda activate 环境名`
    - 运行Jupyter：`jupyter notebook --no-browser --port=目标端口`
    - 复制`token`
    - 直接转到文末的`本地Xshell配置`
    - `注意`：端口号应大于1024，并避开已经启用的端口号，本文采用8000

## 使用配置文件
### 生成配置文件
输入以下命令可以生成Jupyter的配置文件<br>
```
jupyter notebook --generate-config
```
配置文件路径默认在`/root/.jupyter/jupyter_notebook_config.py`

### 生成密钥
启动ipython命令行：
```
$ ipython
```
输入密码，生成密钥：
```
In[1]: from notebook.auth import passwd
In[2]: passwd()
Enter password: 
Verify password: 
Out[2]: 'sha1:0000000000000000000000000000000000000000000000000'
```

### 编辑配置文件
可以输入命令直接进行编辑：
```python3
vim ~/.jupyter/jupyter_notebook_config.py 
```
可以通过Xftp下载配置文件，路径如上，在本地编辑后上传，更方便<br>
具体更改内容如下：
```
c.NotebookApp.allow_remote_access = True
c.NotebookApp.allow_root = True   ## 表示是否允许jupyter使用root权限
c.NotebookApp.ip = '*'  ## 表示允许任意IP访问
c.NotebookApp.port = 8000  ## 可以指定任意端口，注意避开已用端口和公认端口
c.NotebookApp.open_browser = False
c.NotebookApp.password = u'sha1:00000000....' ## 刚刚设置密码时生成的密钥
```
`注意`：配置文件都是注释的，应删除修改行的注释符`#`<br>
端口号应大于1024，并避开已经启用的端口号

## 本地Xshell配置
本地机是Window，需要通过Xshell工具来访问。
* 首先连接上你的服务器
* 在Xshell中，反键会话，进入属性
* 点击连接->SSH->隧道，点击添加

<div align=center><img width = '400' height ='300' src ="https://i.loli.net/2020/03/02/zFQGKuo9cb1IyvD.png"/></div>


`注意`：
* 当类型选择"Local(Outgoing)"的时候，'源主机'表示使用的本地ip地址，可以是localhost也可以是本地内网ip或者公网ip，`侦听端口`填写本地的一个端口
* “目标主机”表示服务器端的ip地址，可以是服务器本地的地址localhost或者是服务器可以访问到的一个ip地址,`目标端口`填写之前配置的端口，本文是`8000`

## 使用Jupyter
* 服务器启动Jupyter Notebook，命令为: `$ jupyter notebook`
* 本地浏览器输入`http://localhost:8888/`，即`源主机:侦听端口`
* 输入之前设置好的密码，即可

![Jupyter登录](https://i.loli.net/2020/03/02/jdC6O21FlzHgYKB.png)

