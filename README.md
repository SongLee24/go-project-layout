# Go项目工程化

一个基本的go项目一般会有三个基础目录：`cmd`, `internal`, `pkg`, `vendor`（可选）。

## /cmd

存放项目的入口代码文件（可编译成可执行程序）。

* 每个可执行程序对应一个文件夹，文件夹的名称 = 可执行程序名称。
* 每个文件夹下必须有一个main包的源文件，文件名称 = 可执行程序名称，当然也可以保留`main.go`。

## /internal

存放私有的应用程序代码，这些是不希望被其他项目导入的代码。可根据实际需求拆分目录。

当然也不要局限根目录下的internal目录，你也可以在任何一个目录中创建internal。

## /pkg

外部项目可以使用的库代码，这里的代码是开放的。所以在将代码放在这里前，一定要三思而行。 毕竟 internal 目录是一个更好的选择来确保项目私有代码不会被其他人导入，因为这是Go强制执行的。

如果你自己或公司的某一个项目，个人的经验，基本上用不上pkg

## /vendor

vendor目录包含了所有第三方依赖的副本，它是go项目最早的依赖包的管理方式。但随着 Go 1.11 引入了 Go Modules，大多数项目都通过`go.mod`和`go.sum`管理项目依赖的版本，不再需要将依赖包下载到本地 vendor 目录。


详情请移步：[golang-standards/project-layout](https://github.com/golang-standards/project-layout/blob/master/README_zh-CN.md)

---

# Gin Web项目工程化

[Gin项目](https://gin-gonic.com/zh-cn/docs/) 目录结构：

```
gin-project-layout/
├── cmd/                     # 应用启动入口
│   └── main.go              # 主程序入口
├── configs/                 # 配置文件存放目录
│   └── config.yaml          # 示例配置文件
├── docs/                    # 文档文件，如 Swagger api 等
├── internal/                # 内部包，存放核心业务逻辑，可根据实际需求拆分目录
│   ├── api/                 # 版本路由
│   ├── app/                 # 包括应用程序启动、初始化等逻辑
│   ├── controller/          # HTTP 请求处理函数
│   ├── middleware/          # 中间件
│   ├── model/               # 数据模型定义
│   ├── repository/          # 数据访问层
│   ├── service/             # 业务逻辑层
│   └── utils/               # 工具函数
├── pkg/                     # 第三方依赖或公共工具包
├── scripts/                 # 脚本文件，如项目部署脚本等
├── tests/                   # 单元测试文件
├── .env                     # 环境变量文件
├── go.mod                   # Go 模块管理文件
├── go.sum                   # Go 模块依赖校验文件
└── README.md                # 项目说明文档
```

参考：
1. [gin-pathway](https://github.com/vespeng/gin-pathway)
2. [Go 项目实战：搭建高效的 Gin Web 目录结构](https://vespeng.com/posts/go_practical_gin_directory_structure/)
