## Git
    git init  // 初始化仓库
    git clone git@github.com:weiwenhuaming411/MyNotes.git  // 克隆远程仓库

    # 个人信息配置: 
        git config --list  // 显示当前git配置信息
        git config --global user.name "MacBook Pro M3"  // 设置提交代码时的用户信息/修改
        git config --global user.email "lushengjin411@gmail.com"  // 设置提交代码时的用户信息/修改
        获取SSH  ssh-keygen -t rsa   enter>>>  // 配置SSH   
            id_rsa.pub

    # 连接仓库
        git remote add origin git@github.com:weiwenhuaming411/MyNotes.git
                            
          // 配置远程连接为origin
        git remote -v  查看远程连接
        git remote remove origin  删除远程连接
        git remote rename old_name new_name  # 修改仓库名

    # 拉取代码
        git pull origin main  // 拉取远程代码与当前分支合并
        git pull <远程主机名> <远程分支名>:<本地分支名>  // 拉取到指定分支
        git pull origin main --allow-unrelated-histories  // 允许不相关历史提交，并强制合并
        git fetch origin main:demo  // 拉取远程代码到本地main并创建一个demo分支
        
    # 上传代码 
        git push origin main
        git push <远程主机名> <本地分支名>:<远程分支名>  // 上传仓库
        git push -u origin main  // 上传至main分支
            -u: 简化之后push操作
            -f: 覆盖
        git push --set-upstream origin 本地:远程  // 关联远程仓库上的分支
        git push origin --delete main  // 删除远程仓库的分支
    
    # 开发操作
        git status  // 查看状态
        git add .  // 跟踪所有文件
        git commit -m "first commit"  // 提交
        git push origin main  // 上传

    # 分支操作:
        git branch name  创建分支
            -v查看所有分支
            -d name删除分支
            -m oldBranch newBranch  分支重命名

        git checkout name  切换分支
            -b name创建并切换

        git merge 主 副  //合并分支



    # 回退版本
        git log --oneline/--graph  //历史提交记录、历史记录何时出现分支合并
        git reset --soft/--hard <hash>  //不带参数(还原)、回退版本、回退并删除之前提交的所有版本

    # 其他操作
        git blame <file>  //查看指定文件修改记录

        git rm <>  //删除文件
        git mv <oldFile> <newFile>  //移动文件/重命名

        git cat-file -p hash  //
        git rm -r -f --cached ./   (删除缓存)

        git diff file1.ext file2.ext  //比较文件的不同
        git diff  显示工作空间和暂存区的差异
        git diff --cached  比较暂存区和提交的差异

    # 代理
        git 开启代理
            git config --global http.proxy http://127.0.0.1:41091
            git config --global https.proxy http://127.0.0.1:41091

        查看代理：
            git config --global --get http.proxy
            git config --global --get https.proxy

        git 取消代理
            git config --global --unset http.proxy
            git config --global --unset https.proxy

        关闭SSI验证
            git config --global http.sslVerify "false"
            git config --global https.sslVerify "false"

    gitee  //国内仓库
    IDEA  //集成仓库