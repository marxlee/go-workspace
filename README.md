# go-workspace
Go橙所需要的依赖

## web应用包

### Redis

#### Redis中国官方网站操作手册
http://redis.cn/

#### 1. import redis-gomodule tool 一个简单的redis链接库
https://github.com/gomodule/redigo/redis

> go get github.com/gomodule/redigo/redis

```
// quickstart
package main

import (
	"fmt"
	"github.com/gomodule/redigo/redis"
)

func main() {
	conn, err := redis.Dial("tcp", "localhost:6379")
	if err != nil{
		fmt.Println("connect err...")
	}
	defer conn.Close()
}
```
#### 2. import redis-module 封装了命令的redis链接库
https://github.com/go-redis/redis

> go get github.com/go-redis/redis/v8

```
// quickstart
import (
    "context"
    "github.com/go-redis/redis/v8"  
)

var ctx = context.Background()

func ExampleNewClient() {
    rdb := redis.NewClient(&redis.Options{
        Addr:     "localhost:6379",
        Password: "", // no password set
        DB:       0,  // use default DB
    })

    pong, err := rdb.Ping(ctx).Result()
    fmt.Println(pong, err)
    // Output: PONG <nil>
}
```









