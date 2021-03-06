## 各个名称介绍



### centos系统

##### 	简介

计算机操作系统

liunx系统发布的版本之一，比较稳定，适合企业级开发。

用作企业服务器，直接用命令行，一般没有界面，

阿里云自带镜像，可直接安装。



------



### 阿里云服务

##### 	简介

提供主机云服务 

注意开放端口



------



### nginx 

##### 	简介

--是个软件，web服务器，用于提供提供高性能的http和反向代理。

----nginx不支持python的wsgi协议，所以用uwsgi做中间件。nginx从浏览器接受请求 将静态请求自己处理，

动态的请求交给uwsgi转给python web框架处理。



##### 	特点

<u>--软件运行内存小，并发强，能不间断运行</u>



##### 	配置方式 	

--**「正向代理」**	**「反向代理」**	**「负载均衡」**		**「动静分离」**	



------



### uWSGI 

###### 简介

[官方文档]: https://uwsgi-docs-zh.readthedocs.io/zh_CN/latest/



--web服务器软件，实现了WSGI，uwsgi、http等协议 nginx中httpUwsgimodule的作用是与uwsgi服务器进行交换。

--wsgi 通信协议 

--uwsgi 线路协议 是uWSGI服务器自有的协议：

--uWSGI实现了uwsgi与wsgi两种协议的web服务器



###### 特点

--超快的性能

--低内存占用

--多app管理

--详尽的日志

--高度可定制

###### wsgi:

--python语言定义的web服务器与web应用程序或框架之间的一种通用接口标准协议/规范，

提高web应用在一些列web服务器之间的移植行

--web服务器与python web应用开发框架有很多种，为了不同的服务器能与不同的应用框架搭配使用，

制定了的一套通信标准。这套标准就是wegi



**标准**：

--wsgi有两方：「服务器」或 「网关」一方，「应用程序」或「应用框架」一方。服务方调用应用方，

提供环境信息，以及回调函数，并接受内web内容作为返回值。

--wsgi中间件同时实现了API的两方，因此在wsgi服务与wsgi应用中间起调节作用。



------

### anconda

##### 简介：

--anconda是一个基于python的环境管理工具

--conda 包管理工具



------



### 正式部署

--一个在本地可以运行的django项目

--购买阿里云后在阿里云使用centos镜像，通过终端远程连接阿里云服务器，在终端操作。

-- 软件之间的结构

![image-20200110152302586](centos%E7%B3%BB%E7%BB%9F%20nginx+uwsgi%20%E9%83%A8%E7%BD%B2Django.assets/image-20200110152302586.png)



##### 一、准备centos服务器

--更新系统软件包	`Yum update -y`

--安装软件管理包和可能使用的依赖 

```
yum -y groupinstall "Development tools"
yum install openssl-devel bzip2-devel expat-devel gdbm-devel readline-devel sqlite-devel
```



**「远程连接」**：mac远程连接报错，记得删除本地的公钥。	`ssh-keygen -R+ip`

**「root目录」**：不要再root目录中创建项目，nginx 与uwsgi 启动会报权限错误



##### 二、安装各个软件包

###### miniconda -包管理

 conda的安装程序，是anconda的小型版本，仅包含conda，python。

[官网]: https://docs.conda.io/en/latest/miniconda.html	"直接选择linux复制链接"

**下载：**在终端输入 `wget -c+连接`  

**安装：**`bash+文件名`  -- 文件默认安装在/root/目录

**启动**：进入文件目录启动环境 `source activate` 

--完成以上步骤后就可以使用conda环境管理包

**仓库**：为conda添加仓库。

--官方仓库	`defaults`

**虚拟环境** : `conda create --name  Django`



###### django 

--简介：python web开发框架,支持python的wsgi协议。

--安装：`conda install Django`		

--**ps**:需要将本地的各种包都要同步安装到服务器的虚拟环境中



###### uWSGI： 

[官网]: https://uwsgi-docs-zh.readthedocs.io/zh_CN/latest/index.html

**--安装** `pip install uwsgi` 	

​		报错：无法建立uwsgi .

​		--添加源 `conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/`

​		--``conda install uwsgi`



**--测试** ：新建text.py文件，然后在http9090端口运行.  **ps:记得在阿里云开放响应端口**

```
def application(env, start_response):
    start_response('200 OK', [('Content-Type','text/html')])
    return [b"Hello World"]
```

```
uwsgi --http :9090 --wsgi-file text.py
```



###### Nginx

--方法一 

**安装**：conda install nginx	**ps:这个软件也是从清华源 conda-forge中下载的**

--安装后地址在 /root/miniconda3/etc/nginx



--方法二：

[官网]: http://nginx.org/en/download.html	"安装稳定版本"

--解压 `tar -xvzf +文件`

--安装 默认安装在usr/local/nginx下

```
 ./configure
make
make install
```





##### 三、将Django项目上传到服务器

--django项目需要在本地能运行

--使用sftp登陆服务器	`put+地址  get+地址`  put上传本地文件 get下载服务器文件	**ps**：需要使用压缩文件

--安装解压文件 `yum install -y unzip zip`

​	解压 `unzip+文件名`





##### 四、uwsgi 启动django

###### django测试: 

--启动django `python3 manage.py rumserver`	  **报错**：缺少第三方包 ，切记一定要先上和线下一定要同步环境。





