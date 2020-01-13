#### **「仓库」**：

--安装仓库	`conda config --add channels`+地址

--查看已经添加的仓库	`conda config --show-sources`

--在文件中修改 `vim ~/.condarc`

--删除库`conda config --remove channels`+ 库名字

--有些仓库已经失效，如果不删除 会报错。

--清华源		直接安装仓库命令+仓库地址（在清华源右键复制）

```
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - defaults 默认源 推荐
  -https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
```





#### 「启动minicounda」**：

--安装mincounda后启动软件 需要在activate目录中

`source activate `



#### **「安装与卸载软件」**：

--安装	`pip install + 软件`

--卸载	 `conda remove + 软件`



#### **「查看软件」**：

--	`conda list` 



#### **「 更新」**： 

--`conda` update +软件



#### **「退出」**：

--	`conda`  `deactivate `



#### **「环境」**：

--查看虚拟环境	`conda env list`

--创建虚拟环境	`conda create --name +名字+python版本`

--删除虚拟环境 `conda remove --name +名字 --all`

