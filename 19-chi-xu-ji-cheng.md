
## 安装jenkins

### 本机安装

1. 安装 Java
> yum install java



环境：CentOS 7.0

```
$ yum install yum-fastestmirror -y  #安装自动选择最快源的插件
#添加Jenkins源:
$ sudo wget -O /etc/yum.repos.d/jenkins.repo http://jenkins-ci.org/redhat/jenkins.repo
$ sudo rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
$ yum install jenkins               #安装jenkins
```


### 主机安装

1. 安装 java 环境
