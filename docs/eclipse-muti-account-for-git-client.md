# Git多个账号的配置和在Eclipse中的应用


+ 在~/.ssh/目录下为每个不同账号生成密钥 

(https://help.github.com/articles/generating-ssh-keys)
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
![image](https://github.com/jadmin/notes/blob/master/assets/0001.png?raw=true)


+ 在~/.ssh/目录下新建config文件(如果没有的话)，配置相关内容

![image](https://github.com/jadmin/notes/blob/master/assets/0002.png?raw=true)

其中Host项是别名，随便取
```
#Host myhost（这里是自定义的host简称，以后连接远程服务器就可以用命令ssh myhost）[注意下面有缩进]
     #User 登录用户名(如：git)
     #HostName 主机名可用ip也可以是域名(如:github.com或者bitbucket.org)
     #Port 服务器open-ssh端口（默认：22,默认时一般不写此行
     #IdentityFile 证书文件路径（如~/.ssh/id_rsa_*)
```

+ 把每个key的公钥添加到git网站上面

+ ssh-add 每个key
```
ssh-add  ~/.ssh/oschina_id_dsa
ssh-add  ~/.ssh/github_id_dsa
```

ssh-add的作用主要将密钥添加到 ssh-agent 的高速缓存中，这样在当前会话中就不需要再次输入密码了
ssh-add -l可以查看句天添加了哪些keys

![image](https://github.com/jadmin/notes/blob/master/assets/0003.png?raw=true)

+ 测试是否配置成功
```
ssh -T git@git.oschina.net
ssh -T git@github.com
```

+ 取消全局账号，并在每个仓库下设置对应的账号邮箱信息
 - 取消global
```
git config --global --unset user.name
git config --global --unset user.email
```

 - 设置每个项目repo的自己的user.email
```
git config  user.name  "xxx"
git config  user.email "xxxx@xxx.com"
```

+ eclipse中配置ssh_home和添加keys列表
 + ssh_home
Eclipse偏好设置->General->Network(Network Connections)->SSH2 home设置 and set your ~/.ssh as SSH Home
 + 对应private keys添加设置
 
![image](https://github.com/jadmin/notes/blob/master/assets/0004.png?raw=true)

