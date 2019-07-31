### go mod 环境配置（IDEA IDE版本）

1. 安装go1.12以上版本，go mod自动集成到go环境中
2. go环境需要配置的环境变量有
   * GOBIN
   * GOROOT
   * GO111MODULE (on/off/auto) go mod需要的特殊设置
   * GOPATH 不必须，go mod会用
   * PATH目录中增加GOBIN，支持命令行

3. 创建go项目，最好遵循gopath的规则，Path/src/ProjectName
4. 在Path/src/ProjectName，创建main包和运行>go mod init <ProjectName> 命令初始化go.mod文件，初始化的go.mod文件内容如下
```
  module prodapi

  go 1.12
```
5. 写入简单的main.go文件（main包）Path/src/ProjectName/main.go
```
package main

import (
    "github.com/gin-gonic/gin"  //这里是需要靠go mod引入包
    "os"
)

func main() {
}
```
5. 运行>go mod tidy命令或者在IDE中go build ProjectName更新go.mod文件，会提示如何进行包的replace
* 命令运行开始前
```
  module prodapi
  go 1.12

  replace (
    golang.org/x/crypto => github.com/golang/crypto latest
    golang.org/x/net => github.com/golang/net latest
    golang.org/x/sync => github.com/golang/sync latest
    golang.org/x/sys => github.com/golang/sys latest
    golang.org/x/text => github.com/golang/text latest
    golang.org/x/tools => github.com/golang/tools latest
  )
```
* 命令运行结束后

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

6. 引入本地包 main.go
```
import (
    "github.com/gin-gonic/gin"
    "os"
    "ProjectName/route"
)
```

### 注意事项
* 当设置GOPATH路径时，go mod安装的模块在GOPATH第一个目录的pkg目录中；当没有设置GOPATH路径是，安装的模块在user目录的go/pkg/...临时目录中
* 在IDEA的GO语言配置下，language>go>go module>开启 enable go modules integration，到此IDEA的go mod配置结束

### 结束，可以愉快的开发GO项目了
