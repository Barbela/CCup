# git 以及 github基本操作总结
## **需要安装的东西**
1. git, 可以在 https://www.git-scm.com 进行下载
2. 如果使用Mac系统，在安装了Homebrew的基础上，直接brew install git 即可

## **其他准备**
1. 注册github帐号

## **初次使用**
1. 首先初始化git， 打开安装好的gitbash ***事实上，如果你使用的是windows系统，那么我们建议在一切情况下，如果要使用命令行操作git，就一定打开gitbash***,  
执行以下语句  
`git config --global user.name "xxxx"` 其中xxxx为你的名字（体现在git提交历史记录中的名字，一般取github注册邮箱的@前面的部分）  
再执行  
`git config --global user.email "xxx@xx.com"` 其中的email地址为你注册的github帐号邮箱
2. 配置github密钥。 github和本地的通信一般使用ssh或者https。方便一点的话就ssh。在gitbash中执行以下命令： 
这一步是生成ssh所使用的密钥对，第二个命令中的邮箱地址是github的注册邮箱地址  
```
cd ~/.ssh
ssh-keygen -t rsa -C "xxx@xx.com"
```  
3. 命令输入后不断回车就可以，直到密钥对生成成功。
4. 生成成功后在.ssh文件夹下，输入ls命令，查看是否生成了id_rsa 和id_rsa.pub两个文件。将id_rsa.pub文件的内容完整拷贝下来，在github的setting->SSH and GPG Keys里，输入为一个ssh密钥。
5. 此时可以在gitbash里测试一下是否可以正确连接github    
`ssh -T git@github.com` 观察输出结果是否正确即可
6. 如果是将github上的已有项目拷贝下来，则`git clone git@github.com:用户名/项目名.git`，如果是在github上新建git项目或者将本地代码库推送上github，则可以直接参照github新建项目后的指南

## **常用git命令**
- `git init` 在当前文件夹下新建一个本地git代码库
- `git config --global user.name "xx"` 以及 `git config --global user.email "xx"` 设定当前使用者的用户名和邮箱
- `git checkout master` 切换到主分支master
- `git checkout -b dev` 新建分支dev
- `git branch` 显示分支列表(不包括未拉取过的远程分支)
- `git branch -a` 显示所有分支列表（包括所有远程分支）
- `git add ./src/main.c` 将当前目录下的src目录下的main.c文件添加进git仓库
- `git add .` 将所有没被添加过的文件都添加进git仓库
- `git commit -m "fix bugs"` 只能在add完成之后执行，将上次提交至今的所有修改提交为一次提交，计入git历史记录
- `git log` 查看提交历史记录，按q退出
- `git log --graph` 图形化展示提交历史记录，按q退出
- `git merge feature/calc` 将feature/calc分支合并进当前分支（feature/calc分支并不会被删除）
- `git reset --hard 35fac82a` 将当前分支回滚回hash值开头为35fac82a的commit（一般先用git log 查看一下想要回滚的提交的hash）
- `git pull` 从远程拉取最新代码
- `git push -u origin master` 将本地的master分支推送到远程，也命名为master（第一次push一个分支时候使用）
- `git push` 第一次操作过之后，后面只需要执行这一句，就可以将当前分支直接推到远程
- `git rm xx` 从git仓库中删除掉不需要的文件

## **注意事项**
- 多查资料,这里是git官方教程，非常好读，中文的 Git官方教程 https://git-scm.com/book/zh/v2
- 写这篇readme的语法叫做markdown，很好学。
- 现在需要熟悉的是git基本操作，但是看看分支开发思想的内容也不错【源代码主干分支开发四大模式】https://blog.csdn.net/zhangmike/article/details/38613429
