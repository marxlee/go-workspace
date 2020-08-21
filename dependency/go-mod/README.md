# GO-MODULES

go module 的思想在于抛弃gopath, 使go项目的依赖完全独立, 缺点是, 不同项目可能使用相同的插件, 没有像mvn那样的中央仓库集中管理插件.

```
# 项目目录

program/
    |-- bin/
    |-- pkg/
    |-- src/
        |-- ..
        |-- go.mod
            |--go.sum
```

## 加入代理, 开启mod
```
# GO111MODULE 是1.11 版本以后加入的内容, 13版本之后是可以不需要设置的
$ export GO111MODULE=on
# 国内代理
$ export GOPROXY=https://goproxy.cn
```

## 如何使用 go mod

### 1. 项目目录下创建go.mod文件
```
# 初始化mod文件, 配合生成go.sum, github.com/xxx/project-go 表示未来提交github后的地址
go mod init github.com/xxx/project-go

# 查看当前依赖项
go list -m add
```
### 2. 加入依赖
```
# 如果项目中已初始化go.mod文件 则执行以下依赖会直接将包加入到本地pkg目录下
go get -u google.golang.org/protobuf/proto

```

