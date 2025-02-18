# 如何本地开发、本地调试
## app 开发者如何本地开发、调试 app
一般有以下几种方案:

- 本地用 docker 启动一个 Layotto sidecar, 或者 docker-compose启动 Layotto+其他存储系统（比如 Redis)
- 公司提供远端 Layotto sidecar

比如在远端测试环境，自己拉起一个 Pod，在里面跑 Layotto sidecar。

1. 如果您能以ip直接访问远端测试环境pod：
    1. 可以把 Layotto ip 修改为上述 Pod ip，本地ip直连pod
2. 如果不能以ip直接访问远端测试环境pod：
    1. 可以将该pod的service类型，设置为`NodePort`或者`LoadBalancer`，本地直连pod service
    2. 可以将该pod注册到gateway，本地直连gateway

开发者在本地调试时，使用以上方式即可实现"本地 app 进程连接到远端 Layotto sidecar"。

更进一步，可以由公司里负责研发环境的团队把上述操作自动化，提供"一键申请远端 sidecar" 功能。

- 如果公司有类似于 github codespace的云端研发环境，那可以在研发环境自带 sidecar


## Layotto 开发者如何本地、开发调试 Layotto
本地编译运行 Layotto 即可