# Jenkins 持续集成体系 

Jenkins 是一个广泛用于持续构建的可视化 web 工具，持续构建说得更直白点，就是各种项目的"自动化"编译、打包、分发部署。jenkins 可以很好的支持各种语言（比如：java, c#, php等）的项目构建，也完全兼容 ant、maven、gradle 等多种第三方构建工具，同时跟 svn、git 能无缝集成，也支持直接与知名源代码托管网站，比如github、bitbucket 直接集成。
简单点说，Jenkins 其实就是大的框架集，可以整个任何你想整合的内容，实现公司的整个持续集成体系！ 

如：自动化，性能，打包，部署，发布&发布结果自动化验证，接口测试，单元测试

Jenkins 可自由部署在各平台：Windows， Linux， Mac

## 安装 Jenkins

### 本机安装 (MAC)
1. 安装 [JavaSDK（Java SE Development Kit）](https://www.jianshu.com/p/9dc3b45fbbec)

2. 架站软体 [MAMP](https://www.mamp.info/en/) or [XAMPP](https://www.apachefriends.org/zh_cn/download.html)

3. 安装 [Jenkins](https://jenkins.io/index.html)

4. 启动 Jenkins，打开浏览器，进入网页 localhost:8080

```
//command line 
设置开机自启动：sudo launchctl load -w /Library/LaunchDaemons/org.jenkins-ci.plist
取消开机自启动：sudo launchctl unload -w /Library/LaunchDaemons/org.jenkins-ci.plist
手动启动：Java -jar jenkins.war
后台启动(默认端口)：nohup java -jar jenkins.war &
后台启动(指定端口)：nohup java -jar jenkins.war -httpPort=88 &
后台启动(HTTPS)：nohup java -jar jenkins.war -httpsPort=88 &
```

如出现连接不到服务器的问题，原因就是 Java 环境有问题，重新配置 Java 环境即可。

5. 配置 Jenkins，[传送门](https://www.jianshu.com/p/9dc3b45fbbec)

6. 卸载 Jenkins

[MAC]
```
//进入以下目录，双击运行
/Library/Application Support/Jenkins/Uninstall.command
//也可以这样运行
sh "/Library/Application Support/Jenkins/Uninstall.command"
//删除配置，这个可选
sudo rm -rf /var/root/.jenkins ~/.jenkinssudo launchctl 
unload /Library/LaunchDaemons/org.jenkins-ci.plistsudo 
rm /Library/LaunchDaemons/org.jenkins-ci.plistsudo 
rm -rf /Applications/Jenkins "/Library/Application Support/Jenkins" /Library/Documentation/Jenkinssudo 
rm -rf /Users/Shared/Jenkinssudo dscl . -delete /Users/jenkinssudo dscl . -delete /Groups/jenkinssudo 
rm -f /etc/newsyslog.d/jenkins.confpkgutil --pkgs | grep 'org\.jenkins-ci\.' | xargs -n 1 sudo pkgutil --forget
//如果使用brew安装的，可以执行以下命令
brew uninstall jenkins
```
[windows]
在控制面板直接删除。

### 主机安装

环境：CentOS 7.0

1. 卸载异常版本 (不可以安装成 gcj(GNU Compiler for the Java Programing Language),导致   jenkins 不工作)
``` 
yum remove java
```

2. 安装 java 环境
``` 
yum install java
```

3. 安装 Jenkins
```
$ yum install yum-fastestmirror -y #安装自动选择最快源的插件
#添加Jenkins源:
$ sudo wget -O /etc/yum.repos.d/jenkins.repo http://jenkins-ci.org/redhat/jenkins.repo
$ sudo rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
$ yum install jenkins #安装jenkins
```

4. 更新jenkins
``` 
yum update jenkins
```

5. 启动服务
```
service jenkins start
```

6. 浏览器访问
```
IP地址:8080
```

更多安装过程细节：[传送门](https://segmentfault.com/a/1190000007086764)

7. 卸载jenkins
使用过程中若出现问题，删了重装是最快的方法
    1. rpm -e jenkins
    2. 会有一些残留的文件分散在各地
    ```
    find / -iname jenkins | xargs -n 1000 rm -rf
    ```




### Jenkins 配置

#### 系统配置文件
> cat /etc/sysconfig/jenkins | more

* `JENKINS_HOME="/var/lib/jenkins"` ,存放 Jenkins 配置及工作文件
* `JENKINS_PORT="8080"`,Jenkins 默认 8080 端口

#### 配置文件夹
> ls /var/lib/jenkins

plugins 文件夹，所有插件都在里面，如插件 ssh-slaves ,会有一个 ssh-slaves 文件夹及 ssh-slaves.jpi。
当某个插件未安装成功时，会有一个以 .tmp 结尾的文件

#### 日志
> /var/log/jenkins/jenkins.log

记录了插件安装等日志，失败信息原因等很清晰，重要


## 其他问题
### 忘记密码
1. 首先，进入 .jenkins 目录（比如/home/jenkins/.jenkins）。
2. 先备份 config.xml 为 config.xml.bak，
3. 而后打开 config.xml 配置文件，修改“<useSecurity>true</useSecurity>”为“<useSecurity>false</useSecurity>”；
4. 同时把“<authorizationStrategy ...>...</authorizationStrategy>”配置删除。
5. 重启之后我们会发现 Jenkins 已经无需登录了。然后，直接找到“系统管理”的“管理用户”菜单，把管理员的密码改回来！
6. 用之前备份的 config.xml.bak 文件覆盖 config.xml 配置文件。
7. 再次重启 Jenkins，终于发现管理员又可以正常登录了。




