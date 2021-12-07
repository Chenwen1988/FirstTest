# Git 实录

[toc]



## 正常使用git的一般流程

1. 本地安装任意版本的[git](https://git-scm.com/)

2. 在远程仓库[github](https://github.com/)上注册

3. 打开git Bash

4. cd到本地需要上传的文件夹，比如`cd D:\LME`

5. 用户名配置，~~这一步好像是非必要的~~

   ```
   git config user.name "chenwen"
   git config user.email "781247552@qq.com"
   ```

6. 本地本家初始化为git库

   ```git
   git init
   ```

7. 添加远程仓库链接

   ```git
   git remote add origin git@github.com:Chenwen1988/greencompanywithfolium.git
   ```

8. 添加本地需要上传的文件

   ```git
   git add .  # 这里默认添加全部文件，这里有坑
   ```

9. 提交文件到暂存库

   ```git
   git commit -m "****"
   ```

10. 合并文件到远程库master分支

    ```git
    git push -u origin master
    ```



## 如何为开源代码做贡献

 [参考](https://opensource.com/article/19/7/create-pull-request-github)

1. Github上找到你感兴趣的项目，Fork到你的Github仓库，生成项目URL地址`https://github.com/<youraccount>/demo `

2. 将项目`clone`到本地

   ```git
   git clone https://github.com/<youraccount>/demo
   ```

3. 创建新的分支并添加远程链接

   ```git
   git check -b new-branch
   git remote add upstream https://github.com/<youraccount>/demo
   ```

4. 然后在本地编辑修改文件并提交

   ```git
   git checkout -b new_branch
   echo “some test file” > test
   git status
   git add test
   git commit -S -m "Adding a test file to new_branch"
   git push -u origin new_branch
   ```

5. Once you push the changes to your repo, the **Compare & pull request** button will appear in GitHub. Click it.

6. Open a pull request by clicking the **Create pull request** button. This allows the repo's maintainers to review your contribution. From here, they can merge it if it is good, or they may ask you to make some changes. 



> In summary, if you want to contribute to a project, the simplest way is to:

1. Find a project you want to contribute to
2. Fork it
3. Clone it to your local system
4. Make a new branch
5. Make your changes
6. Push it back to your repo
7. Click the **Compare & pull request** button
8. Click **Create pull request** to open a new pull request

If the reviewers ask for changes, repeat steps 5 and 6 to add more commits to your pull request.



## git一些其他常用的命令

创建分支 `git branch branch-name`

切换分支 `git checkout branch-name`  创建并切换 `git checkout -b branch-name`



## 使用过程中的一些问题

1. 上传文件权限

   为了传输的安全性，通过SSH链接上传文件需要key来认证，通过以下命令在本地生成公钥和私钥，将公钥（pub结尾的文件）复制粘贴到GitHub账户下Settings -> SSH and GPG keys.

   ```git
   ssh-keygen -t rsa -C "your-email"
   ```

   执行该命令一路按空格，默认设置。

2. 删除远程链接，重新切换新链接

   ```git
   gir remote remove origin
   git remote add origin git@git-url
   ```

3. 撤回add但尚未commit的文件

   撤销部分文件

   ```git
   git reset <filename>
   ```

   撤销全部文件

   ```git
   git rm -r --cached .
   ```

   [详见](https://stackoverflow.com/questions/348170/how-do-i-undo-git-add-before-commit)

4. 合并分支失败