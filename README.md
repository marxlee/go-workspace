# go-workspace
Go橙所需要的依赖

## web应用包

### Redis

#### Redis中国官方网站操作手册
http://redis.cn/

#### import redis tool
> go get github.com/gomodule/redigo/redis

```
// redis connection port 6379 
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






