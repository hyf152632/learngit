基本命令  
在开始前我们还需要了解游戏的一些基本操作：  
play - 默认命令，检查是否过关  
hint - 显示过关提示  
reset - 重启本关，或者重启到指定的某关  
levels - 显示关卡列表  

用git init把管理员文件夹变成了仓库，想删除这个本地仓库？  
sudo rm -rf .git/  

**initialize** an empty repository in it.  
git init  

**Set up your git name and email**, this is important so that your commits can be identified.  
git config   
git config --local user.name andy  
git config --local user.email hyfpersonal@outlook.com  

There is a file in your folder called `README`, you should **add it to your staging area**  
git add 'README'  
>> if want add all files ,use:  
>> git add *  

The `README` file has been added to your staging area, now **commit it**.  
git commit -m ":art:add README"  

**Clone** the repository at https://github.com/Gazler/cloneme  
git clone https://github.com/Gazler/cloneme    

**Clone** the repository at https://github.com/Gazler/cloneme **to `my_cloned_repo`**.  
克隆，同时指定文件夹名  
git clone https://github.com/Gazler/cloneme my_ cloned_repo  

The text editor 'vim' creates files ending in `.swp` (swap files) for all files that are currently open.  
We don't want them creeping into the repository.  
Make this repository **ignore** those swap **files** which are ending in `.swp`.  
vim .gitignore   //然后编辑，添加 "*.swp"  

vim的使用
>> linux命令要小写  
vim filename    //用vim新建或者编辑已有的文件。  
进入到文件中后，按 i 进入编辑模式（insert）。  

退出vim的方法和区别：  
保存退出：  
1.按键盘左上角的"ESC"；  
2.输入“冒号”，即":"(不需双引号)，在下方会出现冒号，等待输入命令，如图，我输入的是WQ。功能如下。  
W：write，写入  
Q：quit，退出  
再回车，就保存退出了  
其实，保存退出还有二个方法：  
A：在最后输入命令时，直接输入"x"，也是一样的，即X=WQ。  
B：最快捷的方法：按了ESC后，直接按shift+zz，或者切换到大写模式按ZZ，就可以保存退出了，即是按2下大写的Z。  

cat 查看文件内容  
ls 文件列表

正常退出：  
正常退出有个前提条件是：打开的文本文件在内容上没有被改动过。  
按了ESC后再输入冒号，在输入命令时，直接输入"q"。  

不保存退出：  
先按ESC，再输入冒号，在输入命令时，直接输入"q!"  

强制退出：  
这个实在是不应该做的操作，因为很操蛋！  
先按ESC，再按冒号，在输入命令时，直接输入"!"  
但退出后，会有提示！  

Notice a few files with the '.a' extension.  We want git to **ignore all but** the 'lib.a' file.  
editor .gitignore:  
*.a  
!lib.a  

There are some files in this repository, one of the files is **untracked**, **which file is it**?
查看所有处于 untracked 状态的文件。使用 git status 查看当前仓库的状态，可以看到红色部分就是 untracked 状态的文件  
git status  

**rm**
There are some files in this repository, **how many** of the files **will be committed**?
查看处于 staged 状态的文件  
git status  

A file has been removed from the working tree, however the file was not removed from the repository.  
Find out what this file was and remove it.  
有一个文件从硬盘中删除了，但是并未从 git 仓库中删除，找到它并从 git 仓库中删除。删除也是修改的一种，提交这个修改就好了  
也就是说，其他的行为导致git仓库状态发生变化，我们只需要更新（提交）git的状态就好。  
git status     //找出变化  
git add  
git commit -m  

**rm_cached**
A file has accidentally been added to your staging area, find out which file and remove it from the staging area.  
*NOTE* Do not remove the file from the file system, only from git.  
将一个新文件从 staging area 中删除。按照要求，不应该直接从硬盘上删除这个文件，只是从 Git 中删除而已。  
加上 --cache 可以是文件只是从 staging area 中移除，不会真正的删除物理文件，  
如果要连这个物理文件也一起删除，请使用 -f 选项  
git rm --cached fileName  

**stash**
You've made some changes and want to work on them later. You should save them, but don't commit them.  
临时提交某个文件。这个操作在需要临时保存修改，而又不想提交的时候特别好用！  
而且 git 中维护了一个栈来保存，所以支持提交多次。如果需要恢复某次提交，使用 git stash apply 即可。  
git stash  

**rename**
We have a file called `oldfile.txt`. We want to rename it to `newfile.txt` and stage this change.  
重命名文件。首先这个文件需要是已经是已追踪状态，才可以使用 git mv 命令，操作完成后自动处于 staging 状态.  
git status  
ls  
git mv oldfile.txt newfile.txt    // 操作完成后自动处于 staging 状态.   
git status  

**restructure**
You added some files to your repository, but now realize that your project needs to be restructured.  
Make a new folder named `src` and using Git move all of the .html files into this folder.  
移动所有 .html 文件到 src 文件夹。git mv 后面的第二个参数可以接受文件或目录，  
如果是目录，则文件会直接放入目录内，可以使用正则（glob模式）匹配所有 .html 文件  
mkdir src  
git mv *.html src  
git status  

On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	renamed:    about.html -> src/about.html
	renamed:    contact.html -> src/contact.html
	renamed:    index.html -> src/index.html

**log**
You will be asked for the hash of most recent commit.  
You will need to investigate the logs of the repository for this.  
git log  

**tag**
We have a git repo and we want to tag the current commit with `new_tag`.  
为最新的 commit 打 tag。不加额外参数就是为当前 commit 记录 tag, 当然可以为特定的 commit 打  
git tag new_tag  

**push_tags**
There are tags in the repository that aren't pushed into remote repository. Push them now.  
将所有本地 tag 都推送到远端。--tags 参数代表将所有的 tags 都推送到远端
git push --tags origin master

**commit_amend**  
The `README` file has been committed, but it looks like the file `forgotten_file.rb` was missing from the commit.  
Add the file and amend your previous commit to include it.  
某个文件在上次提交中遗漏了，在那次提交中补上这个文件。 其实，使用 git commit --amend 会进入编辑界面修改备注信息，我这里直接 :wq 保存并退出  
git status  
git add forgotten_file.rb  
git commit --amend   

**reset**
There are two files to be committed.  The goal was to add each file as a separate commit, however both were added by accident.  
Unstage the file `to_commit_second.rb` using the reset command (don't commit anything).
两个文件都被添加到了 staging area, 但是只想提交其中一个。使用 git reset 可以用仓库中的版本覆盖 staging area 的版本。
git reset 使用仓库中的版本覆盖 staging area 中的，如果 working directory 该文件没有其他修改，则 staging area 中的修改将应用到 working directory 中。  
反之working directory 中的版本将被保留，丢弃 staging area 中的修改。  
git checkout 则是使用 staging area 的中的版本覆盖 working directory。  

git status
git reset HEAD wantToAbandonFileName
git status
git commit -m 'djkd'

**undo the last commit**
You committed too soon. Now you want to undo the last commit, while keeping the index.  
撤销上一次提交。
--soft 参数将上一次的修改放入 staging area
--mixed 参数将上一次的修改放入 working directory
--hard 参数直接将上一次的修改抛弃

git reset --soft HEAD^1  

**Checkout file from the last commit**
A file has been modified, but you don't want to keep the modification.  Checkout the `config.rb` file from the last commit.
抛弃某一次的修改，使用上次提交的版本。checkout 和 reset 的区别参照第二十一关
git checkout fileName

**identify remote**
This project has a remote repository.  Identify it.  
查看远端仓库。其实可以不加-v参数，加这个参数只是可以将地址也一起输出  
git remote 

**remote url**
The remote repositories have a url associated to them.  Please enter the url of remote_location.
git remote -v

**pull** 
You need to pull changes from your origin repository.  
拉取远端仓库。
其实可以指定分支，格式如下
git pull origin remote : local

对应的推送的格式如下
git push origin local : remote

需要注意的两个操作的分支顺序是相反的，记忆的方法很简单，拉取是从远端到本地，所以远端在前，而推送是从本地到远端，所以本地在前。

**remote add**
Add a remote repository called `origin` with the url https://github.com/githug/githug  
添加一个远端仓库  
git remote add origin https://github.com/githug/githug

**push**  
Your local master branch has diverged from the remote origin/master branch. Rebase your commit onto origin/master and push it to remote.  
git push origin master  

**diff**
There have been modifications to the `app.rb` file since your last commit.  Find out which line has changed.  
查看 staging area 和 working directory 中文件的差异。
git diff: 查看 working directory 与 staging area 之间的差异
git diff --cached: 查看 repository 与 staging area 之间的差异
git diff HEAD: 查看 working directory 与 repository 之间的差异

**blame**
Someone has put a password inside the file `config.rb` find out who it was.
查看某个文件的修改人。这个命令简直邪恶，锅终于有人背了！！！  
git blame fileName  

**branch**
You want to work on a piece of code that has the potential to break things, create the branch test_code.  
创建一个分支  
git branch test_code    //创建分支
git branch              //查看分支  

**branch and checkout** 
Create and switch to a new branch called my_branch.  You will need to create a branch like you did in the previous level.  
创建一个分支，并切换过去。其实，git checkout -b my_branch 就是创建一个分支，并切换过去，而且这种方法更方便，平常用的更多  
git branch my_branch
git checkout my_branch  

**checkout_tag**
You need to fix a bug in the version 1.2 of your app. Checkout the tag `v1.2`.  
切换到某个特定的 tag  
git tag   //查看所有的tag
git checkout tagName   //切换到某个特定的tag  

**tag和branch名称有冲突**
You need to fix a bug in the version 1.2 of your app. Checkout the tag `v1.2` (Note: There is also a branch named `v1.2`).  
git checkout tags/tagName  

**branch_at** 
You forgot to branch at the previous commit and made a commit on top of it. Create branch test_branch at the commit before the last.  
根据一个特定的提交创建新分支  
git branch test_branch HEAD^1  

**delete branch**
You have created too many branches for your project. There is an old branch in your repo called 'delete_me', you should delete it.  
git branch -d delete_me  

**push branch** 
You've made some changes to a local branch and want to share it, but aren't yet ready to merge it with the 'master' branch.  
Push only 'test_branch' to the remote repository  
将分支推送到远端仓库  
git push origin test_ branch: test_branch  

**merge**  
We have a file in the branch 'feature'; Let's merge it to the master branch.  
git merge branchName  

**fetch**
Looks like a new branch was pushed into our remote repository.  
Get the changes without merging them with the local repository   
获取远端的修改，但是并不合并到当前分支。其实，git pull 就是 git fetch 和 git merge 组成的。  
git fetch origin  

**rebase**
We are using a git rebase workflow and the feature branch is ready to go into master.  
Let's rebase the feature branch onto our master branch.  
git rebase 一个分支的所有修改在另一个分支上重新应用一遍，所以在提交记录上看，会发现一个分支的所有提交在另一个分支之前或者之后。然后删除另一个被合并的分支，保持分支简洁。
git rebase master feature 表示将 feature 上的修改在 master 上重新应用一遍

git log --graph --all 
git rebase master feature
git status
git checkout feature
git merge master 
在使用此命令的时候，需要非常注意的是，不要 rebase 哪些已经推送到公共库的更新，因为此操作是重新应用修改，  
所以公共库的更新可能已经被其他协作者所同步，如果再次 rebase 这些修改，将可能zh  

**repack**
Optimise how your repository is packaged ensuring that redundant packs are removed.  
将版本库未打包的松散对象打包  
git repack
git repack -d //查看需要打包的文件  

**cherry-pick** 
Your new feature isn't worth the time and you're going to delete it.  
But it has one commit that fills in `README` file, and you want this commit to be on the master as well.  
应用某一个提交的修改。

**git grep**
Your project's deadline approaches, you should evaluate how many TODOs are left in your code  
git grep支持各种条件搜索及正则表达式，平时用的不多，但感觉功能强大  
git grep TODO  

**rename-commit**
Correct the typo in the message of your first (non-root) commit.  
重命名提交。当涉及提交修改时，应该想到 git rebase -i 命令，它接受可以一个参数（提交的哈希值），  
它将罗列出此提交之后的所有提交，然后可以对个个提交做对应的操作  

**git reflog**
git reflog 可以列出所有的操作记录，所以找到之前忘记的信息并不是什么难事

**restore**
You decided to delete your latest commit by running `git reset --hard HEAD^`.  
(Not a smart thing to do.)  You then change your mind, and want that commit back.  
Restore the deleted commit.  

根据之前的经验，git reflog 可以查看所有的操作记录，所以只要能找到误操作之前的 commit id，一样能够恢复现场。  
执行 git reflog 后画面如下，根据操作记录，找到你误操作的之前的 commit id
git reflog 
git checkout commit_id

**conflict**  
You need to merge mybranch into the current branch (master).  
But there may be some incorrect changes in mybranch which may cause conflicts.  
Solve any merge-conflicts you come across and finish the merge.  

冲突处理在平常的协同工作中真是再常见不过了，需要注意的是存在冲突的文件是在 working directory 中的，在解决完冲突之后需要添加到 staging area 并提交。

首先需要提交所有的更改
然后 git merge mybranch  

提示合并冲突
Auto-merging poem.txt
CONFLICT (content): Merge conflict in poem.txt
Automatic merge failed; fix conflicts and then commit the result.
 
然后 vim poem.txt
这个文件中会有提示不同的地方，手动修改，同时删除其中额外的特殊符号。  

然后git add poem.txt
git commit -m 'merge mybranch'
git merge mybranch  




