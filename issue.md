# 问题列表

## Goproxy 代理配置
使用Go命令加载Go代理，请使用cn中国代理提供者
```
go env -w GOPROXY=https://goproxy.cn,direct
```
参考：
```
https://segmentfault.com/a/1190000020293616
https://studygolang.com/topics/9994
https://studygolang.com/articles/29863
https://goproxy.io/zh/
```

## GC 查看
1. 方式1：GODEBUG=gctrace=1
2. 方式2：go tool trace
3. 方式3：debug.ReadGCStats
4. 方式4：runtime.ReadMemStats
