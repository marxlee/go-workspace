#编辑环境变量
vim ~/.bash_profile
#添加如下内容
# GOROOT
export GOROOT=/usr/local/go
# GOPATH 这个目录可以自定
export GOPATH=$HOME/Documents/Go
# GOPATH目录和GOROOT下面的bin目录加入系统环境变量中
export PATH=$PATH:$GOPATH/bin:$GOROOT/bin

作者：adongs
链接：https://ld246.com/article/1565671179978
来源：链滴
协议：CC BY-SA 4.0 https://creativecommons.org/licenses/by-sa/4.0/

#生效
source ~/.bash_profile

# 如果你的mac安装了zsh,需要编辑~/.zshrc文件,在末尾加入如下内容
source ~/.bash_profile

# 输出go版本
go version

1.删除 golang 安装目录

sudo rm -rf /usr/local/go
2.删除如下文件夹

sudo rm -rf /etc/paths.d/go
3.删除环境变量

#编辑环境变量配置,删除所有golang相关的变量
vim ~/.bash_profile
4.检查 golang 残余文件

# 检查golang包
pkgutil --pkgs | grep -i go

# 检查go命令是否存在
which go



