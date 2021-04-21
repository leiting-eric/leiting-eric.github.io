---
title: 搭建静态Hexo博客，部署到github上
---
起因就是想搭一个博客，平时自己工作学习之余能够输出一点东西帮助记忆。

## 具体步骤

### 下载Node.js并安装
#### [官网](https://nodejs.org/en/)找到合适的版本直接下载即可，速度慢的话也可以到国内的镜像站下载。


### 安装淘宝的npm镜像

``` bash
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```

### 安装hexo

``` bash
$ cnpm install -g hexo-cli
```

### 创建blog

``` bash
$ hexo init
```

### 启动博客server
``` bash
$ hexo server
```

### 创建第一篇文章

``` bash
$ hexo new "搭建静态Hexo博客，部署到github上"
```

### 修改内容
#### 找到source文件夹底下的对应的markdown文档，修改其内容即可


### github创建仓库，修改hexo配置文件
#### github中创建对应仓库，然后添加信息到博客文件目录下的_config.yml中
```yaml
deploy:
  type: 'git'
  repo: https://github.com/leiting-eric/leiting-eric.github.io
  branch: master
```

``` bash
$ hexo new "搭建静态Hexo博客，部署到github上"
```

### deploy到github上

``` bash
$ hexo deploy
```

### 打开博客网址，检查内容
#### https://leiting-eric.github.io/

## 踩坑
### repository中看到博客相关代码了，却打不开博客
检查后发现github.io域名下的网站都打不开，猜想可能是DNS污染。
### 解决方案
第一种是修改C:\Windows\System32\drivers\etc文件中的hosts文件，在其中添加一行对应网址的dns解析的结果，例如github就可以填
```txt
13.250.177.223    github.com
```

第二种是修改DNS服务器指向，
```
控制面板> 网络与Internet设置 > 网络共享中心>属性>使用下面的DNS地址
```
我填的是114.114.144.114和8.8.8.8，这两个 dns 都是非商业用途的 dns，解析成功率很高，并且纯净无广告。前一个是国内移动、电信和联通通用的 DNS，是国内用户上网常用的DNS；后一个是 GOOGLE公司提供的 DNS，该全球通用的。

修改好后就可以看到直接看到博客里的内容了。
