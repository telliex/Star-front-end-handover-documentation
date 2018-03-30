# 建立 Jenkins 与 github 通道

## 创建SSH证书

* 终端执行：`ssh-keygen -t rsa -C "xxx@xxx.com"`(邮箱)
* 按回车保存到默认位置，再稍等出来提示输入 passphrase 密码短语，输完按回车要输两遍（它是用来加密私钥，也就是以后使用私钥的时候要输这个密码，或者直接置空）
* 创建成功的SSH 默认路径为 ~/.ssh 目录
* id_rsa 文件存储密钥 ，id_rsa.pub存储公钥

## 添加SSH证书

作法： jenkins 上设置 Credentials，然后再新建job的时候使用设置的 Credentials 即可

1. 在jenkins界面，依次点击： Credentials -> System -> Add domain： 
2. Domain Name: 填写你git服务器的地址，如 github.xxx.com 
3. Description: 随便写一点描述，如 This is the Credential for github
4. 点击 ok 后，在点击 “adding some credentials?”
5. 进入页面后，可以选择 Username with password 或者 SSH Username with private key, 根据你的情况选择，这里我们选择 Username with private key：

   * Username: 随便起一个名字，以便在创建 Job 的时候使用该 Credential 
   * Private Key：可以指定文件，也可以使用默认的 ~/.ssh，当然也可以直接将私钥复制粘贴到此处。 
   * Passphrase: 如果你在创建 ssh key 的时候输入了 Passphrase 那就填写相应的Passphrase，为空就不填写 
   * ID: 空 
   * Description： 空    
6. 新建 Job 就可以看到我们的 Credential 选项了
![jenkins-ssh](/images/jenkins-ssh.jpg)





## github 配置

1. 系统管理 >> 系统设置 >> GitHub Plugin Configuration
   ![](/images/jenkin01.png)
2. github --> setting --> Personal Access Token --> Generate new token
   ![](/images/jenkin02.png)
3. 勾选后，点击Generate token创建一个token。复制这个token。
   ![](/images/jenkin05.png)
   
   自己先保存此token，如果丢失，之后再也无法找到这个token。
4. 回到Jenkins点击Add按钮。贴上 token 。

   ![](/images/jenkin03.png)
5. 点击Verify credentials测试token，显示Credentials verified for user xxx, rate limit: xxxx，说明配置完成了，这样你的Jenkins就具有访问你的github的权限了。
6. 系统管理 --> 系统设置 --> GitHub --> Add GitHub Sever
   ![](/images/jenkin06.png)

## GitHub webhooks 设置
1.  Integration & services --> Add service --> "Jenkins" --> Jenkins(GitHub plugin)
![](/images/jenkin08.png)


2. 进入GitHub上指定的项目 --> setting --> WebHooks&Services --> add webhook --> 输入刚刚部署jenkins的服务器的IP
![](/images/jenkin04.png)


## mail 通知寄送
[通知信寄送设定](https://medium.com/@kuanweilin/%E8%87%AA%E5%8B%95%E5%8C%96%E5%B7%A5%E7%A8%8B%E5%B8%AB%E4%B9%8B%E8%B7%AF-jenkins%E7%9A%84%E8%A8%AD%E5%AE%9A%E8%88%87%E5%AF%A6%E4%BD%9C-9708fe664d08)