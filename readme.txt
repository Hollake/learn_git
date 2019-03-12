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

creating a new branch is quick & simple
