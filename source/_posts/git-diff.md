---
title: 如何使用git diff命令查看差异
---

## 引言

我们知道一个git项目由三个部分组成，工作区(work tree)，暂存区(index area)以及版本库。我们所关注的是文件在这三个部分之间的差别>以及版本库中不同历史提交之间的差别。

![例子](./git-diff/gitSketch.png)

### 常用的四个比较命令：
1. [`git diff [--options] [--] [<path>…​]`](#cmd_1)
2. [`git diff [--options] --cached [<commit>] [--] [<path>…​]`](#cmd_2)
3. [`git diff [--options] <commit> [--] [<path>…​]`](#cmd_3)
4. [`git diff [--options] <commit> <commit> [--] [<path>…​]`](#cmd_4)

### git diff [--options] [--] [<path>…​] <span id="cmd_1">工作区文件和暂存区文件差异:</span>

该命令是用于比较工作区(work tree)中的文件与暂存区(index/staged area)域快照之间的差异， 也就是修改之后还没有暂存起来的变化内容。

``` git
E:\warriorsworld.github.io>git status
On branch sourceCode
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   source/_posts/hello-world.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   source/_posts/hello-world.md
```

例如在上面的操作中，先对hello-word文件内第6行增加一个modified英文单词，然后通过<code>git add .</code>将改动增加到暂存区。然后在第7行增加modify单词。然后输入<code>git diff</code>会看到只有没最后一次修改没有加入到暂存区的差异。

``` git
E:\warriorsworld.github.io>git diff
diff --git a/source/_posts/hello-world.md b/source/_posts/hello-world.md
index 4c0ee2d..41e5f3d 100644
--- a/source/_posts/hello-world.md
+++ b/source/_posts/hello-world.md
@@ -5,7 +5,7 @@ Welcome to [Hexo](https://hexo.io/)! This is your very first post. Check [docume

 ## Quick Start modified

-### Create a new post
+### Create a new post modify

 ``` bash
 $ hexo new "My New Post"  
```
