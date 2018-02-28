
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

### Jenkins 配置

#### 系统配置文件
> cat /etc/sysconfig/jenkins | more

* `JENKINS_HOME="/var/lib/jenkins"` ,存放jenkins 配置及工作文件
* `JENKINS_PORT="8080"`,jenkins默认8080端口