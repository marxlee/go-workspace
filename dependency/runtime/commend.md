# Go 命令解析

### 1. 逃逸追踪
```
# 查看gc变量逃逸到堆heap栈stack
go run -gcflags "-m -l" main.go
```
