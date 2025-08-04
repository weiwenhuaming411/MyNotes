"Patience is key in life。"

git init  // 初始化仓库

git config --list  // 显示当前git配置信息
git config --global user.name "MacBook Pro M3"  // 设置提交代码时的用户信息/修改
git config --global user.email "lushengjin411@gmail.com"  // 设置提交代码时的用

ssh-keygen -t rsa  //获取SSH
    enter>>>  // 配置SSH
    id_rsa.pub

git remote add origin git@github.com:weiwenhuaming411/MyNotes.git  // 链接仓库

git pull origin main  // 拉取远程代码与当前分支合并

git push origin main  // 上传代码