Go 升级安装新版本

```
$ go get golang.org/dl/go1.16.4
$ go1.16.4 download
go1.16.4 version 
```

将 ~/sdk/go1.16.4/bin/go 加入 PATH 环境变量（替换原来的）；  
做一个软连，默认 go 执行 go1.16.4（推荐这种方式），不需要频繁修改 PATH；  
移动 go1.16.4 替换之前的 go（不推荐）；  
