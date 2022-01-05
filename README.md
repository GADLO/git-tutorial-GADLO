# git-tutorial-GADLO
## 使用git
### 1、首先，克隆一个git仓库
克隆一个仓库意味着从源头（在这里就是指 GitHub）上下载所有项目的代码和元数据。使用 git clone <URL> 来克隆仓库。git clone 的作用是下载项目并将其放在你当前工作目录的一个文件夹中。
如果出现错误正克隆到 ‘vulstudy’… fatal: 无法访问
尝试执行：

```git config --global --unset http.proxy```
或
```git config --global --unset https.proxy```
## Git 分支（branch）
  这个 (main) 意味着我们现在位于一个叫做 main 的 分支 上。你可以把一个 Git 分支看作是项目 在某一特定时间点 的副本，可以独立于其他分支进行修改。
## 如何做出我们的第一次提交（commit）
  写书的比喻，让我们创建一个新的文件，命名为 chapter-1.txt 并在其中插入一个句子。

（你可以使用下面的终端命令（terminal command），或者在任何文本编辑器中创建和编辑该文件——这无关紧要。）

```
(main)$ touch chapter-1.txt
(main)$ echo "Chapter 1 - The Beginning" >> chapter-1.txt
(main)$ cat chapter-1.txt
Chapter 1 - The Beginning
```
上面的命令用 touch 创建了一个名为 chapter-1.txt 的新文件，用 echo 和 >> 操作符插入句子“第一章——开端”，并且为了检查我们的工作，用 cat 现实文件内容。

结果是一个里面有一句话的简单文本文件。

让我们再次运行 git status ，看看它的输出有什么不同：

```(main)$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        chapter-1.txt

nothing added to commit but untracked files present (use "git add" to track)```
在这里我们看到一个与之前不同的输出结果。我们看到一个描述“未跟踪文件（untracked file）”的部分，我们的新文件 chapter-1.txt 被列在那里。
  在 Git 开始跟踪（track）一个文件的变化之前，我们首先需要告诉 Git 去跟踪它——正如消息底部所显示的——我们可以用 git add 来实现：

```(main)$ git add chapter-1.txt```
（除了为 git add 制定文件名外，你可以使用（.）来添加目录中的所有修改）。
  让我们再检查一下状态：

```(main)$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   chapter-1.txt

john:~/code/practical-git-tutorial (main)$```
  要提交我们的修改，必须先用 git add 把它们添加到 缓存区（staging area） 。
  接下来，我们需要 git commit 来最终完成提交。
  最佳实践是提供一个详细的信息，说明你做了 那些修改 ——更重要的是——你 为什么 要提交这些修改。

一旦提交历史达到几百或几千条，如果没有一个好的提交信息（commit message）就几乎不可能理解 为什么 会有这些修改。Git 会显示哪些文件有修改，以及这些修改是什么，但这些 修改的意义 要靠我们自己提供。
  
 ## 如何将我们的第一个提交推送（push）到 GitHub
  我们在本地机器上有一个新的提交，我们需要更新我们的“可信单一数据源”—— origin 远端——即 GitHub。

我们目前在本地的 main 分支上，所以我们需要告诉 GitHub 用我们的新提交来更新它自己的 main 。

我们使用 git push 命令做到这一点，我们可以指定 我们要推送到哪里 以及 我们要推送到哪个分支。注意，github更新了推送的安全机制，登录的时候密码是你在github上面生成的token
  ```(main)$ git push origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 326 bytes | 326.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:johnmosesman/practical-git-tutorial.git
   2592324..a8f8b95  main -> main```
这里我们推送到 origin 远端（GitHub）的 main 分支。
输出结果告诉我们 Git 为此所做的一些文件操作，最后一行告诉我们它推送了哪些提交，推送到了哪里。
