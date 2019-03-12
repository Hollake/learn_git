1.先git mkdir foldername 创建foldername的文件夹。

2.接着初始化一个Git仓库，使用git init命令。
添加文件到Git仓库，分两步：
	1.使用命令git add <file>，注意，可反复多次使用，添加多个文件； 例如git add readme.txt。
	2.使用命令git commit -m <message>，完成。 例如 git commit -m "the first commit"。
	如果直接输入git commit 就会进入vi & vim 模式。

3.git status 查看工作区的状态，比如工作区有没有新增文件，或者文件有没有被修改。
	例如 git status readme.txt 。如果返回结果告诉你有文件被修改过，用git diff可以查看修改内容。
	例如 git status 如果在当前目录下文件修改，便会显示
	modified:   readme.txt，新增文件为
	Untracked files: <file>

4.cat readme.txt 读取readme.txt文件内容

5.HEAD指向的版本就是当前版本，HEAD^指上一个版本，HEAD^^指上上一个版本
	因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id,commit_id为git log 所查询的结果。
	1.穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
	2.要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

6.git add <file>是把文件添加到暂存区，git commit 提交更改是将当前更改的文件提交到版本库
	的master分支上，master分支为Git为我们自动创建的唯一分支。
7.乱入一条，vim readme.txt 打开文件编辑，按insert可以选择插入或者替换，按ESC退出
	编辑，接着输入ZZ，保存退出。
8.接着乱入，vi保存时:w，保存退出是:wq，强制退出并忽略所有修改:q!,ZZ也可以保存
	退出。
9.在第一次修改完文件，已经进行git add <file>，接着编辑文件，编辑完成后直接
	commit -m 系统会提出警告，提示此文件夹正在被修改，强行提交只是提交
	第一次add的文件（是否可以强行提交本人不是很清楚），所以在commit file时，
	必须先将修改后的file进行git add <file>，接着进行git commit。
10.命令git checkout -- <file>表示修改后还没有放到暂存区，或者放到暂存区了，经过修改了，
	但是也还没有add添加，那么使用此命令就可以恢复到最近git commit或者git add的状态。
11.接上一条，如果已经add到暂存区了，只剩没有提交怎么办？
	1.用git reset HEAD <file>就可以把暂存区的修改退回到工作区，此时可以
	git status看一下状态，会发现暂存区已经没有可提交的文件，工作区有修改。
	2.既然修改已经退回到工作区，那么就可以用git checkout -- <file>来丢弃工作	区修改.
12.当你要删除文件的时候，可以采用命令：rm test.txt
	这个时候（也就是说这个时候只执行了rm test.txt）有两种情况:
	1.第一种情况:的确要把test.txt删掉，那么可以执行
	git rm test.txt
	git commit -m "remove test.txt",然后文件就被删掉了
	2.文件误删，注意此时只是rm test.txt，还没有commit提交，所以可以执行
	git checkout -- test.txt将文件恢复。
	git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。
13.在GitHub远程仓库建立一个与本地同名的repository仓库，使用
	git remote add origin git@github.com:Hollake/learngit.git就可以将本地仓库和远程仓库关联。
	本地库推送到远程库使用git push -u origin master,即将本地仓库推送到master分支。
	远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。
	在接下来，每次commit以后，有需要都可以进行push。
14.clone到本地仓库，使用git clone git@github.com:Hollake/learn_git.git就可以clone远程仓库到
	你当前路径下。
15.查看当前分支：git branch
	创建分支：git branch <name>
	创建分支：git branch <name>
	切换分支：git checkout <name>
	创建+切换分支：git checkout -b <name>
	合并某分支到当前分支：git merge <name>
	删除分支：git branch -d <name>
16.当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。
	解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。
	用git log --graph命令可以看到分支合并图。
17.通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。
	如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上
	就可以看出分支信息。git merge --no-ff -m "merge with no-ff" dev
18.bug分支，git stash隐藏保存现有工作区内容，切换完成修复其他分支bug后，回到分支，git stash pop
	回到工作现场。
	假如场景是这样的。设A为游戏软件
	1、master 上面发布的是A的1.0版本
	2、dev 上开发的是A的2.0版本
	3、这时，用户反映 1.0版本存在漏洞，有人利用这个漏洞开外挂
	4、需要从dev切换到master去填这个漏洞，正常必须先提交dev目前的工作，才能切换。
	5、而dev的工作还未完成，不想提交，所以先把dev的工作stash一下。然后切换到master
	6、在master建立分支issue101并切换.
	7、在issue101上修复漏洞。
	8、修复后，在master上合并issue101
	9、切回dev，恢复原本工作，继续工作。
19.查看远程库信息，使用git remote -v；
	1.本地新建的分支如果不推送到远程，对其他人就是不可见的；
	2.从本地推送分支，使用git push origin <branch-name>，如果推送失败，说明远程分支比推送的新，所以
	先用git pull抓取远程的新提交，进行本地合并；
	3.没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！
	4.如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git
	 branch --set-upstream-to <branch-name> origin/<branch-name>

20.其他有关git的问题浏览
	https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000
