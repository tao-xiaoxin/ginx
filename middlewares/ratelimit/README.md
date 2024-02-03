# GIN ratelimt middleware
这是一个基于 `GIN` 的限流插件，通过 `redis` 的滑动窗口限流器。
## 使用
首先, 请确保已经安装了 Redis 服务。
接着, 你可以使用以下命令安装 `ratelimit` 中间件插件:
```bash
go get -u github.com/tao-xiaoxin/ginx/middlewares/ratelimit
```
