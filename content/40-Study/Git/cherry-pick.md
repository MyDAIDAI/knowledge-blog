---
UID: 20230512112159 
aliases: 
tags: 
source: 
cssclass: 
created: 2023-05-12
---

## 将其他分支提交的记录合并到当前分支

> 在开发过程中，有时会遇到多个人在同一个分支进行开发，但是分批进行上线的情况，这时就需要新建一个单独的分支，然后将开发分支相关的记录合并到该分支中

要将 A 分支的一个 commit 合并到 B 分支：
1. 切换到A分支`git checkout A`，查看该分支需要进行合并的记录`git log`
2. 切换到B分支`git checkout B`
3. 在B分支上运行命令`git cherry-pick commit_A`