
## 简单介绍

`git rebase`命令在另一个分支基础之上重新应用，用于把一个分支的修改合并到当前分支。

> 翻译成“变基”

**使用语法**

```shell
git rebase [-i | --interactive] [options] [--exec <cmd>] [--onto <newbase>]
    [<upstream> [<branch>]]
git rebase [-i | --interactive] [options] [--exec <cmd>] [--onto <newbase>]
    --root [<branch>]
git rebase --continue | --skip | --abort | --quit | --edit-todo
```

## 使用场景

多人在同一个分支上协作时，很容易出现冲突。即使没有冲突，后push的童鞋不得不先pull，在本地合并，然后才能push成功。

每次合并再push后，分支变得缠绕复杂
![](Pasted%20image%2020230302195601.png)


看上去很乱，为什么Git的提交历史不能是一条干净的直线？

## git rebase  操作

![](Pasted%20image%2020230302195653.png)

```shell
$ git checkout mywork
$ git rebase origin
```

这些命令会把你的”`mywork`“分支里的每个提交(commit)取消掉，并且把它们临时 保存为补丁(patch)(这些补丁放到”`.git/rebase`“目录中),然后把”`mywork`“分支更新 到最新的”`origin`“分支，最后把保存的这些补丁应用到”`mywork`“分支上。

rebase操作的特点：把分叉的提交历史“整理”成一条直线，看上去更直观。缺点是本地的分叉提交已经被修改过了。


在`rebase`的过程中，也许会出现冲突(conflict)。在这种情况，Git会停止`rebase`并会让你去解决冲突；在解决完冲突后，用”`git add`“命令去更新这些内容的索引(index), 然后，你无需执行 `git commit`,只要执行:

```shell
$ git rebase --continue
```

这样git会继续应用(apply)余下的补丁。

在任何时候，可以用`--abort`参数来终止`rebase`的操作，并且”`mywork`“ 分支会回到`rebase`开始前的状态。

```shell
$ git rebase --abort
