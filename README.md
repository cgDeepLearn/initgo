# initgo

<div align="center">
	<br>
	<a href="https://cgdeeplearn.github.io/2020/12/06/init-go" target="_blank">
		<img src="header.svg" width="800" height="400">
	</a>
	<br>
</div>

使用`cookiecutter`初始化go项目模板

[![Build Status](https://travis-ci.org/lacion/cookiecutter-golang.svg?branch=master)](https://travis-ci.org/lacion/cookiecutter-golang)

Powered by [Cookiecutter](https://github.com/audreyr/cookiecutter), Cookiecutter Golang is a framework for jumpstarting production-ready go projects quickly.

## Features | 特性

- Generous `Makefile` with management commands | 使用`MakeFile`
- Uses `go dep` (with optional go module support *requires go 1.11*) | `go dep`可选，go版本需1.11以上
- injects build time and git hash at build time. | 在build时 build时间和git hash 会嵌入到提交中

## Optional Integrations | 可选集成项

- Can use [viper](https://github.com/spf13/viper) for env var config | 可以使用 `viper`做环境变量管理
- Can use [cobra](https://github.com/spf13/cobra) for cli tools | 使用`cobra`做命令行工具
- Can use [logrus](https://github.com/sirupsen/logrus) for logging | 使用`logrus` 做日志记录
- Can create dockerfile for building go binary and dockerfile for final go binary (no code in final container) |`docker`可选
- If docker is used adds docker management commands to makefile
- Option of TravisCI, CircleCI or None

## Constraints | 依赖

- Uses `dep` or `mod` for dependency management | 使用 `dep` 或 `mod`做golang项目的依赖管理
- Only maintained 3rd party libraries are used.

This project now uses docker multistage builds, you need at least docker version v17.05.0-ce to use the docker file in this template, [you can read more about multistage builds here](https://www.critiqus.com/post/multi-stage-docker-builds/).

## Docker | Docker

This template uses docker multistage builds to make images slimmer and containers only the final project binary and assets with no source code whatsoever.

You can find the image dokcer file in this [repo](https://github.com/lacion/alpine-golang-buildimage) and more information about docker multistage builds in this [blog post](https://www.critiqus.com/post/multi-stage-docker-builds/).

Apps run under non root user and also with [dumb-init](https://github.com/Yelp/dumb-init).

## Usage | 使用

Let's pretend you want to create a project called "echoserver". Rather than starting from scratch maybe copying 
some files and then editing the results to include your name, email, and various configuration issues that always 
get forgotten until the worst possible moment, get cookiecutter to do all the work.

First, get Cookiecutter. Trust me, it's awesome: （首先安装`Cookiecutter`）
```console
$ pip install cookiecutter  // 有python环境的可以用python 的pip安装
```

Alternatively, you can install `cookiecutter` with homebrew: (另外如果是mac可以使用`homebrew`安装`Cookiecutter`)
```console
$ brew install cookiecutter
```

Finally, to run it based on this template, type: (使用cookiecutter初始化这个go项目模板)
```console
$ cookiecutter https://github.com/cgDeepLearn/initgo.git //使用github
$ cookiecutter https://gitlab.com/cgDeepLearn/initgo.git //使用gitlab,还有其他也可以添加类似配置
//也可以将此项目fork到其他自己的git平台上，修改对应git用户和地址即可
```

You will be asked about your basic info (name, project name, app name, etc.). This info will be used to customize your new project.
（项目基本信息配置`[ ]`内为默认值）

Warning: After this point, change 'cgDeepLearn', 'cgdeepleanr', etc to your own information.



Answer the prompts with your own desired [options](). For example:
```console
full_name [cgDeepLearn]: cgDeepLearn
git_doamin:
1 - github.com
2 - gitlab.com
Choose from 1, 2, 3 [1]: 1
git_user_group_name [cgdeeplearn]: cgdeeplearn
app_name [mygolangproject]: echoserver
project_short_description [A Golang project.]: Awesome Echo Server
docker_hub_username [cgdeeplearn]: cgdeeplearn
docker_image [cgdeeplearn/docker-alpine:latest]: cgdeeplearn/docker-alpine:latest
docker_build_image [cgdeeplearn/docker-alpine:gobuildimage]: cgdeeplearn/docker-alpine:gobuildimage
use_docker [y]: y
use_git [y]: y
use_logrus_logging [y]: y
use_viper_config [y]: y
use_cobra_cmd [y]: y
Select use_ci:
1 - travis
2 - circle
3 - none
Choose from 1, 2, 3 [1]: 1
```

- 初始化项目示例运行

Enter the project and take a look around: （配置完成后进入项目目录比如我们现在初始化了一个`echoserver`的项目）
```console
$ cd echoserver/
$ ls
```

编译运行

Run `make help` to see the available management commands, or just run `make build` to build your project.
```console
$ make help
$ make build  // 编译
$ ./bin/echoserver  //运行编译生成的二进制文件
```

## Projects build with cookiecutter-golang

- [iothub](https://github.com/lacion/iothub) websocket multiroom server for IoT
