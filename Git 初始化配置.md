
你可以通过以下命令查看所有的配置以及它们所在的文件：

```console
git config --list --show-origin
```

### 用户信息

安装完 Git 之后，要做的第一件事就是设置你的用户名和邮件地址。 这一点很重要，因为每一个 Git 提交都会使用这些信息，它们会写入到你的每一次提交中，不可更改：

```console
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

### 区分大小写

默认情况下git是忽略区分大小写的，多人合作的情况下不规范很容易造成问题，以下是Git大小写敏感的配置方法

##### 开启

全局开启

```javascript
git config --global core.ignorecase false
```

##### 查看

找到 `core.ignorecase=false` 即说明修改完毕

```javascript
git config --list
```


> [Git - 初次运行 Git 前的配置 (git-scm.com)](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE)