## Git+GitHub+Gitte

### Git

https://www.runoob.com/git/git-tutorial.html

### GitHub

https://www.runoob.com/w3cnote/git-guide.html



### 什么是GIT

- Git 是一个开源的分布式版本控制系统



### Git与SVN的qubie

- Git是分布式的，SVN不是
- Git按元数据方式存储，SVN按文件存储
- Git的内容完整性要优于SVN
- Git没有全局版本号，而SVN有（分支在 SVN 中一点都不特别，其实它就是版本库中的另外一个目录）
- Git和SVN的分支不同



### Git的配置

- 配置个人的用户名称和电子邮件地址，这是为了在每次提交代码时记录提交者的信息

  ```bash
  git config --global user.name "scr"
  git config --global user.email 3192355619@qq.com
  ```

- 查看配置信息

  ```bash
  git config --list
  ```

- 生成ssh密钥

  ```bash
  ssh-keygen -t rsa -C "3192355619@qq.com"
  ```

- 验证安装

  ```bash
  git --version
  git config --list
  ```



### Git的相关操作

- 创建仓库

  ```bash
  mkdir my-project
  cd my-project
  git init
  git init newrepo
  ```

- 拷贝项目（repo:Git 仓库；directory:本地目录。）

  ```bash
  git clone <repo> （<directory>）
  ```

- git add filename：添加文件到暂存区中

- git commit：将暂存区中的内容添加到仓库中

- git pull：下载远程代码并合并

- git push：上传远程代码并合并



### Git连接远程仓库

- 添加远程仓库：git remote add [shortname] [url]
- 生成SSH Key：$ ssh-keygen -t rsa -C "songchangran0817@gmail.com"
- 查看远程仓库和实际连接地址：git remote -v