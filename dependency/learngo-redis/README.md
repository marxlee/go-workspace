# Redis Go

## 参考文档(docx):  

1. Redis-go-redis操作指南.docx  
2. Redis-redigo操作指南.docx  

## Redis中国官方网站操作手册
http://redis.cn/

## QuickStart
#### 1. 一个相对底层的redis链接库
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
    // 链接 host + port
	conn, err := redis.Dial("tcp", "localhost:6379")
	if err != nil{
		fmt.Println("connect err...")
	}
	defer conn.Close()
}
```
#### 2. 封装接近命令行cmd的redis链接库
https://github.com/go-redis/redis

> go get github.com/go-redis/redis/v8

```
// quickstart
import (
    "context"
    "github.com/go-redis/redis/v8"  
)

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

#### 3. 使用连接池 redis.Pool

> go get github.com/gomodule/redigo/redis

```
// quickstart
import (
    "context"
    "github.com/gomodule/redigo/redis" 
)

// quickstart
var (
	redisPool *redis.Pool
)

func init()  {
	redisPool = &redis.Pool{
		MaxIdle:     8, // 空闲时最大链接数
		MaxActive:   0, // 最大活动连接数
		IdleTimeout: 100,   // 超时时间 ms
		Dial: func() (redis.Conn, error) {
            // 链接 host+port
			return redis.Dial("tcp", "localhost:6379")
		},
	}
}

func main() {
	conn:= redisPool.Get()
    defer conn.Close()
    // cooding...
}
```

