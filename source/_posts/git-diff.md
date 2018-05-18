---
title: 如何使用git diff命令查看差异
---

## 引言

>     我们知道一个git项目由三个部分组成，工作区(work tree)，暂存区(index area)以及版本库。我们所关注的是文件在这三个部分之间的差别以及版本库中不同历史提交之间的差别。

![例子](./git-diff/gitSketch.png)

### 常用的四个比较命令：
1. [`git diff [--options] [--] [<path>…​]`](#cmd_1)
2. [`git diff [--options] --cached [<commit>] [--] [<path>…​]`](#cmd_2)
3. [`git diff [--options] <commit> [--] [<path>…​]`](#cmd_3)
4. [`git diff [--options] <commit> <commit> [--] [<path>…​]`](#cmd_4)

### git diff [--options] [--] [<path>…​] <span id="cmd_1">工作区文件和暂存区文件差异:</span>

> 该命令是用于比较