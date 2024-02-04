# GIN ratelimt middleware
这是一个基于 `GIN` 的限流插件，通过 `redis` 的滑动窗口实现。
## Usage
首先, 请确保已经安装了 Redis 服务。

接着, 你可以使用以下命令安装 `ratelimit` 中间件插件:
### v1
```bash
go get -u github.com/tao-xiaoxin/ginx/middlewares/ratelimit/v1
```
导入包:
```go
import (
    "github.com/gin-gonic/gin"
    "github.com/redis/go-redis/v9"
    ratelimit "github.com/tao-xiaoxin/ginx/middlewares/ratelimit/v1"
)
```
举个例子:
```go
package main

import (
	"github.com/gin-gonic/gin"
	"github.com/redis/go-redis/v9"
	"github.com/tao-xiaoxin/ginx/middlewares/ratelimit/v1/ratelimit"
	"time"
)

func main() {
	router := gin.Default()
	redisClient := redis.NewClient(&redis.Options{
		Addr: "localhost:6379",
	})
	router.Use(ratelimit.NewBuilder(redisClient, time.Second, 100).Build())
	router.Run(":3342")
}
```