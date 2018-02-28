
## 安装jenkins

### 本机安装









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