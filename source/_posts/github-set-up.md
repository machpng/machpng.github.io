title: 一个客户端设置多个GitHub账号
layout: post
comments: true
categories: Blog
keywords: github

---

最近遇到了这样的需求，需要在一台电脑上同时使用两个github账号，负责不同的用途，所以搜索了一些文章，进行了一下实践。

- 两个github账号
- 取消git全局设置（因为之前设置了全局的git config）
  
  ``` 
  git config --global --unset user.name
  git config --global --unset user.email
  
  ```

- 生成git私钥  
  第一个github账号可以直接回车生成私钥
  ` ssh-keygen -t rsa -C "one@126.com" `
  
  第二个github账号会提示输入文件名，输入与默认配置不一样的文件名。比如: id\_rsa\_two。
  
  ```
  ssh-keygen -t rsa -C "two@126.com"  
  # 之后会提示输入文件名 输入id_rsa_two
  
  ```
  
- github添加公钥  
  分别登陆两个github账号，在 Account Settings 的 SSH Keys 里，点 Add SSH Keys ，将公钥(.pub文件)中的内容粘贴到”Key”中，并输入”Title”.
  
- 执行下面的命令删除所有key  
  `ssh-add -D`  
- 添加ssh key
  
  ```
	ssh-add ~/.ssh/id_rsa
	ssh-add ~/.ssh/id_rsa_two
  ```
   
- 查看ssh key的设置  
  `ssh-add -l`
- 修改 ssh下的config文件
  
  ```
  	cd .ssh
  	touch config
  ```
  
- 配置config文件

  这里必须采用这样的方式设置，否则push时会出现以下错误:
  `ERROR: Permission to two/two.github.com.git denied 	to one.`
  
  ```
	# default
	Host github.com
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa

	# two
	Host two.github.com  # 前缀名可以任意设置
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_two
  ```
	Host名字随意，接下来会用到。  
	其规则就是：从上至下读取config的内容，在每个Host下寻找对应的私钥。这里将GitHub SSH仓库地址中的git@github.com替换成新建的Host别名如：two.github.com
那么原地址是：git@github.com:username/reponame.git
替换后应该是：git@two.github.com:username/reponame.git

- 测试配置是否正确
  
  ```
  ssh -T git@github.com  # 测试github ssh连接
  #Hi ***! You've successfully authenticated, but GitHub does not provide shell access.
  ssh -T git@two.github.com # 测试two.github ssh连接
  #Hi ***! You've successfully authenticated, but GitCafe does not provide shell access.

  ```