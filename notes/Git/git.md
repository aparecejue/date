# Git和gitHub

## Git

* Git使一个**分布式版本控制器**(可避免文件丢失，改错，多人合作不同步导致的后果)
  * **版本控制器**类似数据库，会记录所有对项目文件(任何类型的文件)的更改，进行版本控制
  * 可以**协同工作**(多人编辑文件或代码而不出错)
  * **版本存储**(保存每一次后的版本)
  * **文件备份**(服务器和本地都有完整历史版本)

## GitHub

* GitHub是通过Git进行版本控制的**软件源代码托管服务平台**
  * **代码托管**
  * **学开源项目**
  * **资料库**
  * **多人协作**可管理项目保证文件同步，之后提交合并为完整项目
  * **建博客**GitHub Pages
  * **社交**
  * **简历**
  * **写作**

* 用语

  ![主页](pic\vw.jpg)

  1. **Pull requests**,改进申请
  2. **Issues**,建议
  3. **Marketplace**,应用商店
  4. **Explore**,发现页
  5. **Repository**,仓库(文件夹),一个项目对应一个Repository
  6. **Projects**,项目板，管理项目流程
  7. **Star**,点赞，可用于收藏
  8. **Follow**,关注,人
  9. **Watch**,关注，人或项目，动态会显示在主页面
  10. **Fork**,将GitHub的某个特定仓库（所有文件）原封不动地复制到自己的账户下
  11. **Gist**,代码片段

![项目页面](pic\vdbw.jpg)

# 仓库操作

* 创建
* 提交更改
  * 加备注
  * 更新仓库时，README同步更新
  * **commit**查看历史提交记录

* 查看更改
  * **commit**

* 改名,删除
  * **Setting**

* 改描述
  * **edit**

# Git使用

## 运行前配置

* Git 自带一个`git config`的工具来帮助设置控制 Git 外观和行为的配置变量。
  * 每台计算机上只需要配置一次，程序升级时会保留配置信息。

* 在 Windows 系统中,Git 会查找`$HOME`目录下(一般情况下是`C:\Users\$USER`)的`.gitconfig`文件

* 配置用户信息(用户名，邮箱)(配置完后 `C:\Users\用户名` 目录下，你会找到一个 `.gitconfig` 文件)
  * **查看所有配置**`git config --list`
  * **查看所有配置及其所在文件**`git config --list --show-origin `
  * **配置用户名**`git config --global user.name "用户名"`
  * **配置邮箱**`git config --global user.email "邮箱地址"`
  * **单独查看用户名**`git config user.name`
  * **单独查看用户邮箱**`git config user.email`
    * 果使用了`--global`选项，那么该命令只需要运行一次，因为之后无论你在该系统上做任何事情， Git 都会使用那些信息。 **当你想针对特定项目使用不同的用户名称与邮件地址时，可以在那个项目目录下运行没有`--global`选项的命令来配置。**

* 主要命令

  * **git status**,查看仓库状态

  * **git init**,将文件夹初始化为Git仓库,同时默认进入master(主)分支(初始化master分支)

    ![git-status](pic\ccfw.png)

    1. 正在主分支
    2. 目前还未提交过文件
    3. 提示text.txt文件是Untracked files,即该文件还未提交在git仓库里。

  * **git add “文件名”**,往仓库里添加文件

    * 加入(可提交的列表)(临时缓存区)
    * 可通过`git rm --cached`来移除该缓存

  * **git commit**,将缓存区的改动提交到本地的版本库

  * * 每次使用都会在本地版本库生成一个 40 位的哈希值(commit-id)(这个版本的编号)
    * 相当于版本索引,可通过`git reset`的组合命令回到此处
    * **git commit -m "本次提交信息"**,**-m**代表提交信息,如果不加**-m**是不能直接输入“提交信息”,而是会调出vim来输入提交信息
    * **git commit -a -m "本次提交信息"**,-a 参数可以将**所有**已跟踪文件中的执行修改或删除操作的文件都提交到本地仓库，即使它们没有经过 git add 添加到缓存区
      * 新加的文件(即没有被git系统管理的文件)不能被提交到本地仓库
    * **git commit --amend**,追加提交，在不增加版本号的情况下提交

  * **git log**,打印 Git 仓库提交日志，会显示作者、时间和你写的提交信息
  
  * **git branch**,多人协作，各建分支互不干扰，做完后合并
  
  * * **git branch "分支名"**来新建分支
  
  * **git checkout "分支名"**,用于切换分支
  
  * * **git checkout -b a**，意思是建立分支后自动切换到该分支。
  
  * **git merge**,合并分支
  
  * 1. 切换到master分支
    2. **git merge “分支名”**,合并分支
  
  * **git branch -d "分支名"**,删除分支(该分支还未合并到主分支时无法删除)
  
  * **git branch -D "分支名"**,强制删除分支
  
  * **git tag "版本标签名"**,给版本打上版本号的标签
  
  * * **git tag**,查看标签
    * **git checkout "标签名"**,切换至某一标签

# GitHub下载提交代码

## SSH

* **SSH**,本地与云端之间防止数据泄露的安全机制

* 配置

  1. 生成生成**SSH Key**
     * **ssh-keygen -t rsa**(指定rsa算法生成密钥)
     * ![公钥私钥](pic\KZWEP.png)
  2. 添加**SSH Key**
     * 将 id_rsa.pub 的内容添加到 GitHub 上(公钥)
       * **settings>>SSH and GPG keys>>New SSH key>>add SSH key**
     * 本地的id_rsa密钥跟GitHub上的id_rsa.pub公钥进行配对,授权成功才可以提交代码
  3. 验证绑定
     * **ssh -T git@github.com**

* 下载代码

  * **Download ZIP**
    * 不能实现版本管理
  * **git clone**(cloning with ||SSH)(可实现版本管理)
    * **git clone with HTTPS**,不用SSH能完成(git clone "URL")
    * **git clone with SSH**,(git clone "URL")
  * TTPs 与 SSH 下的 git 都可以直接进行 git clone 操作
  * `HTTPs git clone` 到本地，进行了一些文件的修改，当再次提交到 GitHub远程服务器的时候，都会**进行账号与密码的输入**
  * `SSH git clone` 到本地之后，由于已有 SSH Keys 授权，就**不需要用户名和密码**进行授权了

* 提交代码

  * **git push**,代码更新时，需要把本地的推到远程仓库

  * **git pull**,远程仓库有更新，需要把远程的拉到本地进行合并

    * git clone 和 git pull，虽然它们都是从远程仓库到本地的更新，但前者在本地无仓库时使用，后者是本地已有仓库时使用

      ```text
      git push origin main # 把本地代码推到远程 main 分支
      git pull origin main # 把远程最新的代码更新到本地
      ```

      **一般 push 前会 pull ，不容易冲突**

  * 前提(已有仓库)

  * 把仓库clone到本地,修改后再pull

    * 到这个本地仓库
    * git add(git add --all)
    * git commit
    * git log
    * git push origin **main**(默认向GitHub上的test目录提交了代码,而这个代码是在main分支)

# Git用法

* **git --version**,返回版本号
* **git --help**,帮助文档
* **git config --list**,查看所有配置
* **git config --list --show-origin**,查看所有配置以及它们所在的文件
* **git config --global user.name "用户名"**,全局配置用户名
* **git config --global user.email 邮箱地址**,全局配置邮箱
* **git config user.name**,查看用户名
* **git config user.email**,查看邮箱

```txt
git status ：查看仓库状态
git init：创建一个空仓库，或者重新初始化一个已有仓库
git add：把文件添加到可提交列表（临时缓冲区）
git commit：提交改动（增删改）至仓库
git log：打印提交日志,常规的日志按结构化显示
git branch：查看、添加、删除分支
git checkout：切换分支、标签
git merge：合并分支
git tag：新建、查看标签
git clone：下载仓库
```

* **git diff**：用在git add之前，显示对某一文件的改动

    * git diff <$id1> <$id2> # 比较两次提交之间的差异
    * git diff <branch1>..<branch2> # 在两个分支之间比较
    * git diff --staged # 比较暂存区和版本库差异

* 设置别名

  * `alias`

  * 起别名后，你可以看到 `.gitconfig` 文件里有 `alias` 的配置，如果不需要某个别名，删掉即可

  * ```text
    git config --global alias.别名 git命令
    git config --global alias.ci commit
    git config --global alias.st status
    ```

* 版本回滚

    * **git log**,查看版本号

    * ```text
      在本地时
      git reset --hard 版本号 (抛弃当前工作区的修改)
      git reset --soft 版本号 (回退到之前的版本，但保留当前工作区的修改，可以重新提交)
      ```
      
    * 同步到GitHub
    * ```text      
      git push origin 分支名 (--force)(本地版本落后于远端版本时)
      ```
