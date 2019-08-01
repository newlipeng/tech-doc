### 基本设置


### 安装和部署

### 路径安排
> /cmd

cmd目录存放main.go文件

> /configs

configs目录存放项目相关的配置文件，项目配置在apollo中，因此和apollo相关

> /controller

controller控制层逻辑代码，一些简单的逻辑在这里处理，调用/service项目逻辑

> /internal

internal目录存放项目本身使用的公共类，公共方法

> /middleware

middleware目录存放第三方中间件

> /models

models目录存放，和api，db的通讯放在这里

> /route

route目录存放路由相关文件，路由规则

> /service

service目录存放主要的项目逻辑
