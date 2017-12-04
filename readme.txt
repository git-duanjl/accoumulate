7.3 命令 :采用ssh加密进行传输
            7.3.1. 如果主目录下没有.ssh 输入 $ ssh-keygen -t rsa -C "youremail@example.com" 进行创建

            7.3.2  本地仓库 ：

    			git config --global user.name git-duanjl
    			git config --global user.email 1025470552@qq.com
    			(Git 分布式版本控制系统，需要自报家门，注：git config 命令的 --global 参数，表示这台机器上所有Git仓库都会使用这个配置，也可以对某个仓库指定不同的用户名和Email)

    			mkdir git-workspace (创建版本库 git workspace)
    			git init （把这个目录变成Git可以管理的仓库）

        			ls -a 查看隐藏文件
        			rm -rf .git 删除版本库
        			touch readme.txt 添加txt文件
        			vim readme.txt 查看文件
        			:q! 退出编辑器

    			git add readme.txt 	添加到stage(缓存)
    			git commit -m "do some writing" 把文件提交到仓库 

    			git status 查看文件状态
    			git log 查看修改记录
    			git log --pretty=oneline 简化查看

    			git reset --hard head^ 回退 上个版本head^，上上个版本head^^ ,上30个版本head~30
    			cat readme.txt 查看内容。
    			git reflog 查看所有版本操作。
    			git diff 查看之前连续操作
    			git diff hard -- readme.txt 查看工作区和版本库里面最新版本的区别
    			git checkout -- readme.txt 放弃工作区修改

            7.3.3 远程仓库 ：
                注册githup （本人无服务器） 
                采用ssh加密进行传输
                    1. 如果主目录下没有.ssh 输入 $ ssh-keygen -t rsa -C "youremail@example.com" 进行创建
                    2. 打开https://github.com 左上角有settings --- SSH and GPG keys --- New SSH key
                    3. .ssh --- id_rsa.pub 里面的内容复制到 key 里，title 随便写。
                    3. 创建repository  new repository --- 在repository name 里给你仓库起个名字 --- create 
                    4. 关联仓库 git remote add origin xxxxxxxxxxxxx(ssh github地址)
                    5. 把本地库的的所有内容推送到远程仓库上
                        git push -u origin master : 在 github 上就能看到同步的文件。
                        由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
                    6. git clone git@github.com:git-duanjl/accoumulate.git 克隆一个本地库
            7.3.4 分支管理 ： 
                    1.创建并切换 git checkout -b dev
                        相当于 git branch dev
                               git checkout dev 

                    2.查看 git branch *代表当前分支
                    查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>

ceshi ceshi