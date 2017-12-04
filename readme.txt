7.3 命令 :采用ssh加密进行传输
    7.3.1. 如果主目录下没有.ssh 输入 $ ssh-keygen -t rsa -C "youremail@example.com" 进行创建
    7.3.2  本地仓库 (command)：
            git config --global user.name git-duanjl
            git config --global user.email 1025470552@qq.com
            (Git 分布式版本控制系统，需要自报家门，注：git config 命令的 --global 参数，表示这台机器上所有Git仓库都会使用这个配置，也可以对某个仓库指定不同的用户名和Email)

            mkdir git-workspace (创建版本库 git workspace)
            git init （把这个目录变成Git可以管理的仓库）

                ls -a （查看隐藏文件）
                rm -rf .git （删除版本库）
                touch readme.txt （添加txt文件）
                vim readme.txt （查看文件）
                :q! （退出编辑器）

            git add readme.txt  添加到stage(提交到缓存)
            git commit -m "do some writing" （提交到仓库 ）

            git status (查看仓库状态)
            git log (查看记录)
            git log --pretty=oneline (简化查看)

            git reset --hard head^ （回退上个版本 注:上个版本head^，上上个版本head^^ ,上30个版本head~30）
            cat readme.txt （查看内容）
            git reflog （查看所有版本操作。）
            git diff （查看之前连续操作）
            git diff hard -- readme.txt （查看工作区和版本库里面最新版本的区别）
            git checkout -- readme.txt （放弃工作区修改）

    7.3.3 远程仓库 (command AND add repository)：
            **注册githup （本人无服务器） 
            **采用ssh加密进行传输
            1. ssh-keygen -t rsa -C "youremail@example.com" （如果本地分目录下没有.ssh 执行该条命令去创建）
            2. settings --- SSH and GPG keys --- New SSH key （添加SSH key）
            3. .ssh --- id_rsa.pub（SSH key）
            3. new repository （创建新的远程仓库），repository name（远程仓库名） 
            4. git remote add origin xxxxxxxxxxxxx (关联远程仓库)
            5. git push -u origin master (把本地仓库推送到远程仓库)
                 : 在 github 上就能看到同步的文件。
                由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
            6. git clone git@github.com:git-duanjl/accoumulate.git （克隆到本地仓库）

    7.3.4 分支管理 (command)： 
            1.git checkout -b dev （创建并切换到该分支）
                1.1 git branch dev （创建dev分支）
                1.2 git checkout dev  （切换到dev分支）
            2.git branch （查看分支  *代表当前分支）
            3.合并分支
                3.1 git checkout master (切换到合并到的分支 master) 
                3.2 git merga dev （合并 dev 到当前分支） 
            4.git branch -d dev （删除分支）
            5.git merge --no-ff -m "af" dev (显示合并dev分支可查看记录)
            6.git --graph --pretty=oneline --abbrev-commit (查看记录)
            7.git branch -D dev (强制删除分支。场景：你在一个分支开发新功能现在不要了，不能合并只能强删)
            8.多人协作
                8.1 git remote (查看远程仓库信息)
                8.2 git remote -v (详细)
                8.3 git push origin *** (推送***分支到远程仓库，master代表主分支--也就意味着整体推送--)
                    8.3.1 git pull (如果push失败，证明repository已经更新，需要git pull 与本地仓库合并。
                          如果有冲突修改，没有则继续push)
                    8.3.2 git branch --set-upstream dev origin/dev (创建本地分支和远程分支链接。注: pull 提示“no tracking
                          information”,执行该command)
    7.3.5 标签 (git tag) :
            1.git tag v1.0 （创建标签）
            2.git tag(查看所有标签)
            3.git tag v1.0 622457 (指定 commit id, git log --pretty=oneline --abbrev-commit : 查看commit id)
            4.git show v1.0 (查看v1.0)
            5.git tag -a v1.0 -m "该版本添加****" commit_id （创建带说明的标签）
            6.git tag -d v1.0 (删除标签)
            7.git push origin v1.0 (推送到远程仓库)
            8.git push origin :refs/tags/v1.0 (删除远程仓库tag)