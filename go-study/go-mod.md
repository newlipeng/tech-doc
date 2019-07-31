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
5. 更新go.mod文件
