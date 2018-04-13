# github使用方法
* 建立链接
* 常见的`git`命令
* `git`的复杂使用
* 分值操作

---
## 建立链接

现在我已经默认你已经有了一个`github`的账号,然后开始创建一个新的仓库：<br>
1. 点击`New repository`
2. 填写相关的信息`Repository name`
3. 确认`Create repository`

这样一个新的仓库就建好了<br>
为了确保我们在每一台电脑上都可以`clone`这份代码，接下里我们需要将github账号和电脑建立关联
1. 打开本地终端，输入：
```
    ssh-keygen -t rsa -b 4096 -C "xx@example.com"
```
2. 一直确认下去，在本地得到一个`ssh`文件夹。这样一个文件夹保存了我们的公钥和私钥<br>
`id_rsa.pub`&ensp;&ensp;&ensp;**用于存放公钥**<br>
`id_rsa`&ensp;&ensp;&ensp;**用于存放私钥**<br>

我们需要打开我们个人设置，找到`SSH and GTP keys`,创建一个新的`New GPG key`,将公钥的内容复制到新的`GPG key`中,这样我们的电脑和仓库就建立了链接，接下里可以使用相关的命令行操作将本地的代码推送到远程的`github`仓库中。

---

## 常见的`git`命令

3种状态：
1. `mommitted`:已提交该文件已经被安全的保存在本地数据中
2. `modified`: 修改了某个文件，但还没有提交保存
3. `stagged`: 把已经修改的文件放在下次提交时要保存的清单中

起步：

初次使用你需要设置的姓名和邮箱
```
    git config --global user.name 'you name'
    git config --global user.email xxx@example.com
```
将github上的项目克隆到本地，变为本地仓库
```
    git clone 项目的ssh地址
```
添加文件并提交<br>
* 创建文件
```javascript
    touch a.md   
```
* 查看当前文件的状态（是否提交）
```
    git status
```
* 提交到暂存区
```
    git commit -v //添加注释
    git commit -am "xxx" //自动添加注释
```
* 上传到远程仓库
```
    git push     //如果提示失败，可以尝试下面操作
    git push origin master
```
* 如果远程仓库没有更新，在push之前我们要执行pull操作(远程仓库的变动更新合并到本地仓库)
```
    git pull
```
* 删除一个文件
```
    rm -rf a.md
    git add . 
    git commit -am "删除a.md"
```

---

## 复杂使用
空文件夹提交到远程仓库
```
    echo "# hello" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin 远程仓库的地址
    git push -u origin master
```

1. 将`hello`写入到`README.md`文件中
2. 初始话本地仓库
3. 上传到暂存区
4. 添加注释
5. 将本地仓库链接到远程仓库
6. 暂存区文件上传到远程仓库的主分支上

查看本地仓库里记录的远程仓库的地址
```
    git remote -v
```
强制推送（覆盖别人的代码）
```
    git push -f origin master
```
在添加一个远程库的标签
```
    git remote add gitlab ssh地址
```
推送到`gitlab`标签的地址上
```
    git push gitlab master
```
删除`gitlab`标签
```
    git remote remove gitlab
```
修改`origin`标签对应的地址
```
    git remote set-url origin ssh地址
```
---
## 分支操作

分支可以想象成多人协作，每个独立的负责的人负责当前分支的开发，后来的人在前面的支出上在开出分支.如果没有分支的操作，可能导致的后果是项目不能同时进行，延长了开发的期限

* 查看当前分支
```
    git branch -a
```
* 创建本地`dev`分支
```
    git branch dev
```
* 切换到`dev`分支
```
    git checkout git dev
```
在分支上创建的文件在主分支是查看不到的,只有在分支上可以查看得到<br>

分支推送到远程仓库
```
    git push origin dev
```
分支到主分支上
```
    git merge dev
```
进行完上述步骤，还要推送到远程主分支上。

### 冲突
当自己和别人改同一个文件的同一个地方的时候，执行git pull时更新本地合并时出现冲突的解决方案
1. 修改冲突文件
2. 重新提交
