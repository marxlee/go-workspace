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
		MaxIdle:     8,
		MaxActive:   0,
		IdleTimeout: 100,
		Dial: func() (redis.Conn, error) {
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

