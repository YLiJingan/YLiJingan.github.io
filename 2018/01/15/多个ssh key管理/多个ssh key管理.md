---
title: 多个SSH KEY 以及 HEXO
comments: true
tags: ['ssh key','hexo']
---
### 多个SSH KEY的管理
多ssh-key模式 是开发时可能遇到的问题，自己之前在使用多 ssh key 模式时不知所措,今天配置好了，记录下来。
#### github提交验证机制
使用一下命令生成ssh	   
`$ ssh-keygen -t rsa -C "youremail@email.com"`	
这里需要我们输入生成的公钥和私钥路径，默认是~/.ssh/id_rsa,由于我之前已经有一个Key了，这里我进行了路径自定义，以防止覆盖之前生成的key。
![](http://ow4f5k7el.bkt.clouddn.com/ssh.png)		
这时会在用户根目录下生成一个.ssh文件夹，一个私钥：id_rsa，一个公钥：id_rsa_pub，该公钥和私钥包含了你邮箱的信息，具有随机不可复现性！

**在输入路径之后，Enter passphrase默认是空值，这里直接回车就好了。如果在这里输入了，那么每次push提交代码的时候，都需要输入你在这里输入的字符串**

****
ssh公钥私钥同时生成且唯一配对。公钥用于远程主机，私钥存储在本地工作机，私钥用于在push（即write操作）时验证身份。因为公钥与私钥的唯一对应性，只有能和公钥配对的私钥才能对远程主机进行写操作！

我们在使用github时会发现有两个地方牵涉到公钥添加，一个是账号设置下的ssh setting，另一个是单个仓库设置的Deploy key。添加至前者则代表 私钥主机可对当前远程主机的所有仓库进行写操作，添加至后者则代表 私钥主机只能对当前仓库进行写操作。

每次连接时SSH客户端发送本地私钥（默认~/.ssh/id_rsa）到远程主机进行公私钥配对验证！


#### 多个 SSH key 管理
1. 生成多个key			
	~/.ssh文件夹
	![](http://ow4f5k7el.bkt.clouddn.com/~:.ssh%E6%96%87%E4%BB%B6%E5%A4%B9.png)
2. 在github远程添加公钥
3. 新建config文件，用于配置各个公私钥对应的主机。未设置的将使用默认的私钥。   
   `cat config`
	![](http://ow4f5k7el.bkt.clouddn.com/config.png)    
	![](http://ow4f5k7el.bkt.clouddn.com/ssh_config.png)
4. 测试连接情况      
   `ssh -T git@second.github.com`   
   ![](http://ow4f5k7el.bkt.clouddn.com/git%20ssh%E6%B5%8B%E8%AF%95.png)
   如上情况，则测试成果。之后我们可以向之前一样使用就好了
   
   ******
   
   
  以上操作都完美执行之后，在进行push的时候，出现了如下所示的错误。
  ![](http://ow4f5k7el.bkt.clouddn.com/chmod.png)
  需要执行`chmod 0600 /User/.ssh/id_rsa_ylijingan`修改私钥的权限	
  
  
### 迁移HEXO
#### MAC命令行 解压rar
1. 使用Homebrew安装unrar    
	`brew install unrar`    
2. 解压文件    
	`unrar x 需解压的文件目录 `   
	
#### hexo	迁移过程 [传送门](https://www.zhihu.com/question/21193762) 
1. 安装 git   
2. 按照上述内容添加ssh key   
3. 安装 node  
4. 安装hexo `npm install hexo-cli -g`   
5. 拷贝原来文件夹的内容
	* **必须保留** 
		* _config.yml(自己修改的站点配置文件)
		* theme/(主题文件夹)
		* source/(自己写的博客文件)
		* scaffolds/(文章模板)
		* package.json
	* **可以删除(.gitignore 中的内容)**
		* node_modules/
		* .git/
		* public/(hexo g会重新生成)
		* .deploy_git/(hexo d会重新生成)
		* ...
		
6. 文件夹下，npm install
7. hexo g
8. hexo d --没有报错，即转移成功!👌👌👌
	

	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	