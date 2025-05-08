---
date: 2023-05-14 12:15:49
url:
tags:
title: git 代理
en-title:
---

#### 仅为 GitHub 设置代理

##### git 代理
设置 `git config --global http.https://github.com.proxy socks5://127.0.0.1:1086`  
设置完成后, `~/.gitconfig` 文件中会增加以下条目:
```
[http "https://github.com"]
    proxy = socks5://127.0.0.1:1086
```

##### ssh 代理
修改 `~/.ssh/config` 文件
```
Host github.com
    User git
    ProxyCommand nc -v -x 127.0.0.1:1086 %h %p
```


[WSL2 的 2.0 更新彻底解决网络问题](https://zhuanlan.zhihu.com/p/657110386)

[ GitHub 设置代理] (https://gist.github.com/chenshengzhi/07e5177b1d97587d5ca0acc0487ad677)

# [git 设置和取消代理](https://www.cnblogs.com/xueweihan/p/7242577.html)

```verilog
# 设置ss
git config --global http.proxy 'socks5://127.0.0.1:1080'

git config --global https.proxy 'socks5://127.0.0.1:1080'

# 设置代理
git config --global https.proxy http://127.0.0.1:1080

git config --global https.proxy https://127.0.0.1:1080

# 取消代理
git config --global --unset http.proxy

git config --global --unset https.proxy
```