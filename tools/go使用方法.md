go 使用方法

# 安装

## windons安装

安装包下载：https://golang.google.cn/dl/

### 使用github下载安装go的其他插件

#### 1、环境变量：

GoPath环境变量：用于设置Go语言的工作空间目录。（请注意，Go 1.11版本及更高版本引入了Go模块（Go Modules）的概念，可以在任何目录下工作，而不需要依赖于GoPath环境变量）

GOROOT环境变量：用来指定Go语言的安装目录。它应该指向你安装Go语言的根目录。

#### 2、安裝插件：

在GOROOT环境变量设置的目录下创建src、bin、pkg，在src目录下创建golang.org/x

进入${GoPath}\src\golang.org\x下，依次执行以下命令：
git clone https://github.com/golang/lint.git lint
git clone https://github.com/golang/tools.git tools
git clone https://github.com/golang/mod.git
git clone https://github.com/golang/xerrors.git
（注意：${GoPath}\src\golang.org\x下应该是空目录，如果有存在与git下载重名目录，可能会导致下载失败）

命令都执行成功后，可以看到${GoPath}\src\golang.org\x下目录有以下子目录：

cd切换到src目录：${GoPath}\src下，再依次执行以下三条命令进行安装：
go install golang.org/x/lint/golint@latest
go install golang.org/x/tools/cmd/gorename@latest
go install golang.org/x/tools/cmd/guru@latest

| 程序名     | URL                                  | 程序用途                                                    |
| ---------- | ------------------------------------ | ----------------------------------------------------------- |
| dlv        | github.com/derekparker/delve/cmd/dlv | go语言调试工具                                              |
| gocode     | github.com/stamblerre/gocode         | go语言代码检查、自动补全                                    |
| godef      | github.com/rogpeppe/godef            | go语言代码定义和引用跳转                                    |
| golint     | golang.org/x/lint/golint             | go语言代码规范检查                                          |
| go-outline | github.com/ramya-rao-a/go-outline    | 用于在go源文件中提取json形式声明的简单工具                  |
| gopkgs     | github.com/uudashr/gopkgs/cmd/gopkgs | 快速列出可用包的工具                                        |
| gorename   | golang.org/x/tools/cmd/gorename      | 在go源代码中执行标识符的精确类型安全重命名                  |
| goreturns  | github.com/sqs/goreturns@latest      | 类似fmt和import的工具，使用零值填充go返回语句以匹配返回类型 |
| go-symbols | github.com/acroca/go-symbols         | 从go源码树中提取json形式的包符号的工具                      |
| gotour     |                                      | go语言指南网页版                                            |
| guru       | golang.org/x/tools/cmd/guru          | go语言源代码有关工具，如代码高亮等                          |



## linux 安装

