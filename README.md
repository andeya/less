# less

Less is a command line tool facilitating development with lessgo framework. It is modified from bee.

## Requirements

- Go version >= 1.3.


## Installation

Begin by installing `less` using `go get` command.

```bash
go get github.com/henrylee2cn/less
```

Then you can add `less` binary to PATH environment variable in your `~/.bashrc` or `~/.bash_profile` file:

```bash
export PATH=$PATH:<your_main_gopath>/bin
```

> If you already have `less` installed, updating `less` is simple:

```bash
go get -u github.com/henrylee2cn/less
```

## Basic commands

Less provides a variety of commands which can be helpful at various stage of development. The top level commands include: 
```base
  new         create an application base on lessgo framework
  run         run the app which can hot compile
```

## less new

Creating a new lessgo web application is no big deal, too.

```bash
$ less new myapp
[INFO] Creating application...
/home/zheng/gopath/src/myapp/
/home/zheng/gopath/src/myapp/common/
/home/zheng/gopath/src/myapp/middleware/
/home/zheng/gopath/src/myapp/static/
/home/zheng/gopath/src/myapp/static/tpl/
/home/zheng/gopath/src/myapp/static/css/
/home/zheng/gopath/src/myapp/static/js/
/home/zheng/gopath/src/myapp/static/img/
/home/zheng/gopath/src/myapp/static/plugin/
/home/zheng/gopath/src/myapp/uploads/
/home/zheng/gopath/src/myapp/router/
/home/zheng/gopath/src/myapp/sys_handler/
/home/zheng/gopath/src/myapp/sys_handler/admin/
/home/zheng/gopath/src/myapp/sys_handler/admin/login/
/home/zheng/gopath/src/myapp/sys_model/
/home/zheng/gopath/src/myapp/sys_model/admin/
/home/zheng/gopath/src/myapp/sys_view/
/home/zheng/gopath/src/myapp/sys_view/admin/
/home/zheng/gopath/src/myapp/sys_view/admin/login/
/home/zheng/gopath/src/myapp/biz_handler/
/home/zheng/gopath/src/myapp/biz_handler/home/
/home/zheng/gopath/src/myapp/biz_model/
/home/zheng/gopath/src/myapp/biz_view/
/home/zheng/gopath/src/myapp/biz_view/home/
/home/zheng/gopath/src/myapp/middleware/test.go
/home/zheng/gopath/src/myapp/static/img/favicon.ico
/home/zheng/gopath/src/myapp/static/js/jquery.js
/home/zheng/gopath/src/myapp/static/js/jquery.min.map
/home/zheng/gopath/src/myapp/router/sys_router.go
/home/zheng/gopath/src/myapp/router/biz_router.go
/home/zheng/gopath/src/myapp/sys_handler/admin/index.go
/home/zheng/gopath/src/myapp/sys_handler/admin/login/index.go
/home/zheng/gopath/src/myapp/sys_model/admin/login.go
/home/zheng/gopath/src/myapp/sys_view/admin/login/index.tpl
/home/zheng/gopath/src/myapp/biz_handler/home/index.go
/home/zheng/gopath/src/myapp/biz_handler/home/websocket.go
/home/zheng/gopath/src/myapp/biz_view/home/index.tpl
/home/zheng/gopath/src/myapp/biz_view/home/websocket.js
/home/zheng/gopath/src/myapp/biz_view/home/jquery.githubRepoWidget2.js
/home/zheng/gopath/src/myapp/biz_view/home/index.css
/home/zheng/gopath/src/myapp/main.go
2016/08/08 15:45:47 [SUCC] New application successfully created!
```

## less run

To run the application we just created, navigate to the application folder and execute `less run`.

```bash
$ cd myapp
$ less run
```


## Help

If you happend to forget the usage of a command, you can always find the usage information by `less help <command>`.

For instance, to get more information about the `run` command:

```bash
$ less help run
usage: less run [appname] [watchall] [-main=*.go]

start the appname throw exec.Command

then start a inotify watch for current dir
                    
when the file has changed less will auto go build and restart the app

  file changed
       |
  check if it's go file
       |
     yes     no
      |       |
 go build    do nothing
     |
 restart app

```

## lessgo project

```
─Project 项目开发目录
├─config 配置文件目录
│  ├─app.config 系统应用配置文件
│  └─db.config 数据库配置文件
├─common 后端公共目录
│  └─... 如utils等其他
├─middleware 后端公共中间件目录
├─static 前端公共目录 (url: /static)
│  ├─tpl 公共tpl模板目录
│  ├─js 公共js目录 (url: /static/js)
│  ├─css 公共css目录 (url: /static/css)
│  ├─img 公共img目录 (url: /static/img)
│  └─plugin 公共js插件 (url: /static/plugin)
├─uploads 默认上传下载目录
├─router 源码路由配置
│  ├─sys_router.go 系统模块路由文件
│  ├─biz_router.go 业务模块路由文件
├─sys_handler 系统模块后端目录
│  ├─xxx 子模块目录
│  │  ├─example.go example操作
│  │  └─... xxx的子模块目录
│  └─... 其他子模块目录
├─sys_model 系统模块数据模型目录
├─sys_view 系统模块前端目录 (url: /sys)
│  ├─xxx 与sys_handler对应的子模块目录 (url: /sys/xxx)
│  │  ├─example.tpl 相应操作的模板文件
│  │  ├─example2.html 无需绑定操作的静态html文件
│  │  ├─xxx.css css文件(可有多个)
│  │  ├─xxx.js js文件(可有多个)
│  │  └─... xxx的子模块目录
├─biz_handler 业务模块后端目录
│  ├─xxx 子模块目录
│  │  ├─example.go example操作
│  │  └─... xxx的子模块目录
│  └─... 其他子模块目录
├─biz_model 业务模块数据模型目录
├─biz_view 业务模块前端目录 (url: /biz)
│  ├─xxx 与biz_handler对应的子模块目录 (url: /biz/xxx)
│  │  ├─example.tpl 相应操作的模板文件
│  │  ├─example2.html 无需绑定操作的静态html文件
│  │  ├─xxx.css css文件(可有多个)
│  │  ├─xxx.js js文件(可有多个)
│  │  └─... xxx的子模块目录
├─database 默认数据库文件存储目录
├─logger 运行日志输出目录
└─main.go 应用入口文件
```

