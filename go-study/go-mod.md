### go mod 环境配置（IDEA IDE版本）

1. 安装go1.12以上版本，go mod自动集成到go环境中
2. go环境需要配置的环境变量有
   * GOBIN
   * GOROOT
   * GO111MODULE (on/off/auto) go mod需要的特殊设置
   * GOPATH 不必须，go mod会用
   * PATH目录中增加GOBIN，支持命令行

3. 创建go项目，最好遵循gopath的规则，Path/src/ProjectName
4. 在Path/src/ProjectName，创建main包和运行>go mod init <ProjectName> 命令初始化go.mod文件
```
  module prodapi

  go 1.12
```
5. 更新go.mod文件
```
  module prodapi

  go 1.12

  replace (
    golang.org/x/crypto => github.com/golang/crypto v0.0.0-20190701094942-4def268fd1a4
    golang.org/x/net => github.com/golang/net v0.0.0-20190724013045-ca1201d0de80
    golang.org/x/sync => github.com/golang/sync v0.0.0-20190423024810-112230192c58
    golang.org/x/sys => github.com/golang/sys v0.0.0-20190730183949-1393eb018365
    golang.org/x/text => github.com/golang/text v0.3.2
    golang.org/x/tools => github.com/golang/tools v0.0.0-20190730215328-ed3277de2799
  )

  require github.com/gin-gonic/gin v1.4.0  
```
