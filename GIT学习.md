## GIT版本控制系统 



> 版本控制系统：   
>> 1.记录历史版本信息（记录每一次修改的记录）  
> 2.方便团队相互之间协作开发  
> ....  

> 常用版本控制系统：  
>>  1. cvs/svn:集中式版本控制系统 
> 2. git:分布式版本控制系统


##GIT工作原理
+ 工作区：我们能看到的，并且能用来写代码的区域
+ 暂存区：临时存储用的
+ 历史区：生成历史版本    

	工作区-> 暂存区 ->历史区  

**1.GIT的全局配置**

>  第一次安装完成git后，在全局环境下配置基本信息：我是谁？  

``` 
git config -l   查看配置信息
git config --global -l	查看全局配置信息
配置全局信息：用户名和密码
$ git config --global user.name 'xxx'
$ git config --global user.email 'xxx@xx.xx'
```

**2.创建仓库完成版本控制**

> 创建本地git仓库  

```
$ git init 
// -->会生成一个隐藏文件夹“.git”(不能删除，因为暂存区和历史区还有一些其他的信息都放在这里，删除了就是完整的git仓库)
```

> 在本地编写完成代码后（在工作区）把一些文件提交到暂存区

```shell
$ git add xxx	把某个文件或者文件夹都提交到暂存区
$ git add ./-A	把所有最新修改的文件都提交到暂存区	//‘/’表示或者
$ git status 查看当前文件的状态（红色代表在工作区，绿色代表在暂存区，看不见证明所有修改的信息都已经提交到历史区）
```

> 把暂存区内容提交到历史区  

```
$ git commit -m'描述信息：本次提交内容的一个描述'
查看历史版本信息（历史记录）
$ git log
$git reflog		包含回滚的信息
```

> 将历史信息回滚到工作区

```shell
$ git reset --hard xxx	//'xxx'为提交commit码，如下面所示：		
	$ git log
	commit 4213d3f7af6480bfccbf5925e59a7d1fcd3b62f0 (HEAD -> master)
	Author: josengit <q18882025526@163.com>
	Date:   Tue Feb 4 21:43:45 2020 +0800
    新增加了1.txt

```







## GIT和GITHUB



> Git-hub:https://github.com
>
> 一个网站（一个开源的源代码管理平台），用户注册后，可以在自己的账户下创建仓库，用来管理项目的源代码（源代码是基于git传到仓库中的）
>
> 我们所熟知的插件、类库、框架都在这个平台上有托管，我们可以下载观看和研究源码等

**1.settings用户设置**

+ Profile修改自己的基本信息
+ Account 可以修改用户名
+ Security 可以修改自己的密码
+ Emails 邮箱（必须进行邮箱校验）
+ ....

**2.创建仓库**

new repository->填写信息->Create repository

- public 公共仓库作为开源项目
- private 私有仓库作为团队内部管理的项目

Settings->删除仓库Delete this repository

​			->Collaborators设置协作开发的人员

Code 可以查看历史版本信息和分支信息

**3.把本地仓库信息提交到远程仓库**

```shell
//建立本地仓库和远程仓库的链接
$ git remote -v				//查看本地仓库和哪些远程仓库保持链接
$ git remote add origin [GIT远程仓库地址]		//让本地仓库和远程仓库新建一个链接origin是随便起的一个链接名（可以自行修改，不过一般都用这个）
$ git remote rm origin 		//删除与远程仓库的链接
```

```shell 
$ git pull origin master		//提交之前最好先拉取
$ git push origin master		//将本地代码提交到远程仓库（提交时需要输入密码）
```

```shell
$ git clone [远程仓库git地址][别名：可以不设置，默认是仓库名]
/*
 *真实开发流程：
 *	1.组长或者负责人先创建中央仓库(增加协作者)
 *	2.小组成员基于$ git clone把远程仓库及默认内容克隆到本地一份（一个克隆解决了三个事情：初始化一个本地	git仓库‘git init’、和对应的远程仓库也保持了关联‘git remote add’、把远程仓库默认内容拉取到本		地‘git pull’）
 *	3.每个组员写完自己的程序后，基于‘git add/git commit’把自己修改的内容放到历史区，然后通过‘git 	pull/git push’把自己本地信息和远程仓库信息保持同步即可（可能涉及冲突的处理）
 */
```

