1.先git mkdir foldername 创建foldername的文件夹。

2.接着初始化一个Git仓库，使用git init命令。
添加文件到Git仓库，分两步：
	1.使用命令git add <file>，注意，可反复多次使用，添加多个文件； 例如git add readme.txt。
	2.使用命令git commit -m <message>，完成。 例如 git commit -m "the first commit"。
	如果直接输入git commit 就会进入vi & vim 模式。

3.git status 查看工作区的状态，比如工作区有没有新增文件，或者文件有没有被修改。
	例如 git status readme.txt 。如果返回结果告诉你有文件被修改过，用git diff可以查看修改内容。

4.cat readme.txt 读取readme.txt文件内容

5.HEAD指向的版本就是当前版本，HEAD^指上一个版本，HEAD^^指上上一个版本
	因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id,commit_id为git log 所查询的结果。
	1.穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
	2.要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。