# Lab0: GitLab

Due: 30 Sep, 23:59:59

## TODO

1. 认真阅读[文档](https://ics-26fall-fdu.github.io/labs/lab0-git-lab/)，学习 Git 的基本用法，并在报告中回答文档中的问题。（15 分）

    - 你之前有过多人协同开发的经历吗？如果有，你们是使用什么方式分工协作的？

        答：之前基本以独立开发为主，没有过真正意义上的多人协同开发经历；以往小组合作时主要是各自写好后通过聊天软件或网盘互传文件、手动合并，常出现版本混乱、互相覆盖的问题。通过本实验系统学习 Git，希望掌握分支管理、合并与冲突解决等多人协作所需的技能。

    - 思考一下，Git 为什么要设计“暂存-提交”两个步骤？

        答：Git 把一次提交拆成“暂存（git add）”和“提交（git commit）”两步，主要好处有：① 选择性提交：可只把部分改动加入暂存区、其余留在工作区，让每次提交聚焦一个主题、更“原子”；② 提交前可检查：暂存后可用 git diff --cached 查看即将提交的内容，确认无误再提交；③ 细粒度控制：git add -p 甚至能只暂存文件里的部分代码块（hunk）；④ 工作区与版本库解耦：工作区里未完成的中间状态不会被被动记录，只有主动 add 的内容才会进入提交。简言之，暂存区决定“这次提交什么”，提交步骤才真正把快照记录下来。

    - `git branch` 和 `git branch -a` 的区别是什么？查阅资料并回答。

        答：`git branch` 只列出本地分支；`git branch -a`（`--all`）列出本地分支 + 远程跟踪分支（`remotes/origin/...`）。远程跟踪分支是 Git 在本地保存的远程仓库状态镜像，不联网也能查看（`git branch -r` 则只列出远程跟踪分支）。下面的输出直观展示了区别：

    ```bash
        (base) gary@LAPTOP-1P7N3FS9:/mnt/c/Users/wsq/Desktop/26Fall/ics/ICS-GitLab$ git branch
        * main
        (base) gary@LAPTOP-1P7N3FS9:/mnt/c/Users/wsq/Desktop/26Fall/ics/ICS-GitLab$ git branch dev
        (base) gary@LAPTOP-1P7N3FS9:/mnt/c/Users/wsq/Desktop/26Fall/ics/ICS-GitLab$ git branch -a
        dev
        * main
        remotes/origin/HEAD -> origin/main
        remotes/origin/main
    ```

2. 使用此仓库建立个人仓库，完成 `main.c` 文件中的 `TODO` 部分并进行一次 commit。（50 分）

   - 只要填入任意字符串就算完成，当然你也可以随意发挥（程序的正确性不纳入计分，有修改即可）。

   - 如果你想要编译运行 `main.c`，执行

   ```bash
   make
   ./main
   make clean
   ```

3. 在下面的三个网页中任选其二进行阅读，简要概括其内容，并谈谈你对“为什么要学习 Git”这个问题的理解。（15 分）

    - [Commit Message 规范](https://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)
    - [Git Flow 分支控制](https://www.dafaycoding.com/article/git-gif-flow)
    - [语义化版本](https://semver.org/lang/zh-CN/)

4. 学习 Git 分支管理，新建 `feature` 分支，在该分支以及 `main` 分支上对 `main.c` 分别进行一次修改与提交（10 分）。随后将 `feature` 分支 merge 到 `main` 分支（即切换回 main 分支执行 `git merge feature`），并处理发生的合并冲突（10 分）。

    - 在两个分支上的提交必须要满足：在 `main` 分支合并时会出现冲突。请你解决这个冲突，并在实验报告里截图表明你遇到并解决了冲突。

    - 请阅读 `git merge` 部分，思考如何修改 `main.c` 会出现冲突。

    - 如果你两次提交之后合并没有出现冲突，不必担心，你可以不用撤回之前的提交，而是继续尝试提交修改并 merge，直到出现冲突并解决。

5. 在 `main` 分支提交一份实验报告（实验报告单独评分），格式要求为 `PDF` 或 `Markdown`。内容包括：

    - 文档中要求回答的问题
    - 你的实验步骤
    - 必要的截图
    - 你的建议（可选）
