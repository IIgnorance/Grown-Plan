# git 基础

## Git是分布式版本控制系统

分布式版本控制系统根本没有“中央服务器”，每个人的电脑上都是一个完整的版本库，这样，你工作的时候，就不需要联网了，因为版本库就在你自己的电脑上。既然每个人电脑上都有一个完整的版本库，那多个人如何协作呢？比方说你在自己电脑上改了文件A，你的同事也在他的电脑上改了文件A，这时，你们俩之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。
 
## Git 工作流程

一般工作流程如下：

克隆 Git 资源作为工作目录。
在克隆的资源上添加或修改文件。
如果其他人修改了，你可以更新资源。
在提交前查看修改。
提交修改。
在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。

## Git 工作区、暂存区和版本库

工作区：就是你在电脑里能看到的目录。
暂存区：英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

[!](http://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg)

在版本库中标记为 "index" 的区域是暂存区（stage, index），标记为 "master" 的是 master 分支所代表的目录树。
"HEAD" 实际是指向 master 分支的一个"游标"。
当对工作区修改（或新增）的文件执行 "git add" 命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。
当执行提交操作（git commit）时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。
当执行 "git reset HEAD" 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。
当执行 "git rm --cached <file>" 命令时，会直接从暂存区删除文件，工作区则不做出改变。
当执行 "git checkout ." 或者 "git checkout -- <file>" 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。
当执行 "git checkout HEAD ." 或者 "git checkout HEAD <file>" 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。

## Git 基本操作

git init <directory>: 以目录建仓库
git add <file> : 添加文件至暂存区
git commit <file> : 提交修改        -m : 提交说明 -a : z
git status : 查看当前工作区状态  -s : 获得简短的结果输出
git diff <file> : 查看修改
git log : 显示从最近到最远的提交日志
git reflog : 查看命令历史
git reset --hard commit_id[HEAD^] : 版本重置(master游标切换)
git reset HEAD <file> : 暂存区重置
git checkout -- <file> : 暂存区全部或指定的文件替换工作区的文件
git checkout HEAD <file> : 暂存区工作区重置
git clone <repo> <directory> <Name>: 从现有 Git 仓库中拷贝项目
git rm <file> : 删除工作区暂存区文件
