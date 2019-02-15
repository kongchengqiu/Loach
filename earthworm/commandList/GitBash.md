#### 常用 Git 命令清单

1. git init        // 当前目录新建一个Git代码库
2. git clone [url]   // 下载一个项目
3. git config --list // 显示当前的Git配置
4. git commit -m "代码提交的信息"  // 提交暂存区到仓库区
5. git commit -a  // 提交工作区自上次commit之后的变化，直接到仓库区
6. git commit -v // 提交时显示所有改变的信息
7. git branch -r // 列出所有远程分支
8. git branch -a // 列出所有本地分支和远程分支
9. git checkout [branch-name] // 切换到指定分支，并更新工作区
10. git merge [branch] // 合并指定分支到当前分支
11. git branch -d [branch-name] // 删除分支
12. git push origin [branch-name] // 分支推送到远端仓库
12. git push origin --delete [branch-name] // 删除远程分支
