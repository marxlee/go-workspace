# Protobuf

## 简介
protobuf是Google开发的一种数据描述语言，能够将结构化的数据序列化，可用于数据存储，通信协议等方面,官方版本支持Go, C++, Java, Python，社区版本支持更多语言。

* 相对于JSON和XML具有以下优点：

* 体积小: 消息大小只需要XML的1/10 ~ 1⁄3

* 速度快: 解析速度比XML快20 ~ 100倍

* 集成度高： 使用Protobuf的编译器,可以生成更容易在编程中使用的数据访问代码

* 更好的兼容性： Protobuf设计的一个原则就是要能够很好地向下或向上兼容

## 安装
####  1. 从 https://github.com/protocolbuffers/protobuf/releases 获取Protobuf编译器protoc
```
wget https://github.com/protocolbuffers/protobuf/releases/download/v3.6.1/protobuf-all-3.6.1.tar.gz

tar zxvf protobuf-all-3.6.1.tar.gz

cd protobuf-3.6.1/

./configure

make

make install

安装完毕，测试是否安装成功

protoc --version

可能报错：

protoc: error while loading shared libraries: libprotoc.so.17: cannot open shared object file: No such file or directory

解决办法：

export LD_LIBRARY_PATH=/usr/local/lib/

然后再protoc --version，可以看到

libprotoc 3.6.1

安装成功！
```

#### 2. 获取 goprotobuf 提供的 Protobuf 插件 protoc-gen-go（保存到 $GOPATH/bin 下，$GOPATH/bin 应该被加入 PATH 环境变量，以便 protoc 能夠找到 protoc-gen-go）

此插件被 protoc 使用，用与边缘 .proto 文件为 Golang 原文件（.proto->.pb.go），通过此原文件（.pb.go）可以使用定义在 .proto 文件中的消息。
```
go getgithub.com/golang/protobuf/protoc-gen-go

cd $GOPATH/src/github.com/golang/protobuf/protoc-gen-go

go build

go install

vi ～/.bashrc 

將$GOPATH/bin 加入環境變量:

export PATH=$PATH:$GOPATH/bin

source ～/.bashrc
```

#### 3. 获取 goprotobuf 提供的支持库，包括序列号（marshaling）、反序列化（unmarshaling）等功能
```
go get github.com/golang/protobuf/proto

cd $GOPATH/src/github.com/golang/protobuf/proto

go build

go install
```

#### 4. 创建proto编译文件
order.proto
```
syntax = "proto3";
package message;

//订单请求参数
message OrderRequest {
    string orderId = 1;
    int64 timeStamp = 2;
}

//订单信息
message OrderInfo {
    string OrderId = 1;
    string OrderName = 2;
    string OrderStatus = 3;
}

//订单服务service定义
service OrderService{
    rpc GetOrderInfo(OrderRequest) returns (OrderInfo);
}


# 编译文件
$ protoc --go_out=. *.proto

# 如果定义的.proto文件，如本案例中所示，定义中包含了服务接口的定义，而我们想要使用gRPC框架实现RPC调用。
# 开发者可以采用protocol-gen-go库提供的插件编译功能，生成兼容gRPC框架的golang语言代码。
# 只需要在基本编译命令的基础上，指定插件的参数，告知protoc编译器即可。
# 具体的编译生成兼容gRPC框架的服务代码的命令如下：
$ protoc --go_out=plugins=grpc:. *.proto

# 亦或 注意, 内部import一定要正确
protoc --proto_path src/ --go_out=src/ src/pb/*.proto

# 使用go-rpc生成文件: [proto_path]路径src/protos下的所有.proto文件, [go_out]地址为:./src/pb_go
protoc --proto_path=./src/protos ./src/protos/*.proto --go_out=plugins=grpc:./src/pb_go

```