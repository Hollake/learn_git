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
