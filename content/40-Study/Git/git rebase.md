---
UID: 20230512112246 
aliases: 
tags: #git
source: 
cssclass: 
created: 2023-05-12
---

## 变基

在`Git`中整合来自不同分支的修改主要有两种方法：`merge`和`rebase`，那么两种有什么区别呢
x

## 



## 使用场景
### 删除某个中间的提交记录

> 在做项目时，有可能会遇到想删除某个中间的提交记录，这个提交记录之后也有人提交，但是不能删除掉之后提交的代码记录

1. `git log`获取`commit`信息 
2. `git rebase -i (commit-id)`, `commit-id` 为要删除的`commit`的下一个`commit`号 
3. 编辑文件，将要删除的`commit`之前的单词改为`drop`
4. 保存文件退出大功告成 
5. `git log`查看

比如我的提交历史如下，我现在想删除commit_B，但是不影响commit_B之后的提交历史
```
commit_C
commit_B 
commit_A
```

操作方法如下：
1. 首先找到commit_B提交之前的一次提交的commit_A
2. 执行如下命令 `git rebase -i commit_A`
3. 将下图中`commit_B`这一行前面的`pick`修改为`drop`，保存退出
![[Pasted image 20230505132520.png]]
4. 至此已经删除了指定的`commit`，可以使用`git log`进行查看
5. 使用`git push origin HEAD --force`强制推送至远程仓库