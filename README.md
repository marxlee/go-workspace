# go-workspace
Go橙所需要的依赖



## web应用包
### Redis

> go get github.com/gomodule/redigo/redis

```
// redis connection port 6379 
conn, err := redis.Dial("tcp", "localhost:6379")
if err != nil{
	fmt.Println("connect err...")
}
defer conn.Close()

```

### Redis中国官方网站
http://redis.cn/




