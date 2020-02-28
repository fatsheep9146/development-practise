# bashrc 实践

编辑 \~/.bashrc \~/.bash_profile 文件设置常用命令


## 常见用法

### alias

```
alias tosrc="cd /Users/zhaoziqi/go/src"
```

### function

定义可以指定参数的常见命令


```
myfunction() {
    #do things with parameters like $1 such as
    mv "$1" "$1.bak"
    cp "$2" "$1"
}

myfunction old.conf new.conf #calls `myfunction`
```

参考链接

1. [https://stackoverflow.com/questions/7131670/make-a-bash-alias-that-takes-a-parameter](https://stackoverflow.com/questions/7131670/make-a-bash-alias-that-takes-a-parameter)
2. [https://askubuntu.com/questions/626458/can-i-pass-arguments-to-an-alias-command](https://askubuntu.com/questions/626458/can-i-pass-arguments-to-an-alias-command)


