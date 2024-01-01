# Git的使用

### 第一章 快速入门

​		想要让git对一个目录进行版本控制需要一下步骤：

#### 第一阶段 （单枪匹马）

> - 进入要管理的文件夹
>
> - 执行初始化命令
>
>   `git init`
>
> - 管理目录下的文件状态
>
>   `git status`
>
>   ==注意：==新增的文件和修改过后的文件都是红色的
>
> - 管理指定文件（红变绿）
>
>   `git add 文件名`
>
>   `git add .`
>
> - 个人信息配置：用户名，邮箱（一次即可）
>
>   `git config --global user.email "邮箱"`
>
>   `git config --global user.name "名字"`
>
> - 生成版本
>
>   `git commit -m "描述信息"`
>
> - 查看版本记录
>
>   `git log`

![image-20231231082614929](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20231231082614929.png)

<img src="C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20231231082648449.png" alt="image-20231231082648449" style="zoom: 50%;" />

#### 第二阶段：拓展新功能

`git add`

`git commit -m '短视频'`

#### 第三阶段：“约饭事件”

- 回滚至之前版本

  `git log`

  `git reset --hart 版本号`

- 回滚至之后的版本

  `git reflog`

  `git reset --hard 版本号`

- 额外的功能：
  - `git checkout 文件名`从修改区（红色）到原始区
  - `git reset HEAD 文件名`从暂存区（绿色）到修改区（红色）
  - `git reset --mix 版本号`从版本号直接回到修改区（红色）
  - `git reset --soft 版本号`从版本库回到暂存区（绿色）

#### 总结

```python
git init
git add
git commit
git log
git reflog
git reset --hard 版本号
```

#### 第四阶段：商场&紧急修复bug

1. 分支

   分支可以给使用者提供多个环境，意味着你可以把你的工作从开发主线上分离开来，以免影响开发主线

2. 紧急修复bug方案

   ![image-20231231101341704](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20231231101341704.png)

3. 命令总结

   - 查看分支

     `git branch`

   - 创建分支

     `git branch 分支名称`

   - 切换分支

     `git checkout 分支名称`

   - 分支合并（可能产生冲突）

     `git merge 要合并的分支`

     ==注意：==切换分支再合作

   - 删除分支

     `git branch -d 分支名称`
   
4. 工作流：

   <img src="C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20231231144808291.png" alt="image-20231231144808291" style="zoom:33%;" />
   
   

#### 第五阶段  进军三里屯

在家里上传代码

> 1. 给远程仓库起别名
>
>    `git remote add origin 远程仓库地址`
>
> 2. 向远程推送代码
>
>    `git push -u origin 分支`

到公司新电脑上第一次获取代码

> 1. 克隆远程仓库代码
>
>    `git clone 远程仓库地址（内部已实现git remote add origin 远程仓库地址）`
>
> 2. 切换分支
>
>    `git checkout 分支`



在公司进行开发

> 1. 切换到dev分支进行开发
>
>    `git checkout dev`
>
> 2. 把master分支合并到dev[仅一次]
>
>    `git merge master`
>
> 3. 修改代码
>
> 4. 提交代码
>
>    `git add .`
>
>    `git commit -m 'xx'`
>
>    `git push origin dev`

回到家中继续写代码

> 1. 切换到dev分支进行开发
>
>    `git checkout dev`
>
> 2. 拉代码
>
>    `git pull origin dev`
>
> 3. 继续开发
>
> 4. 提交代码
>
>    `git add .`
>
>    `git commit -m 'xx'`
>
>    `git push origin dev`

在公司继续开发

> 1. 切换到dev分支进行开发
>
>    `git checkout dev`
>
> 2. 拉代码
>
>    `git pull origin dev`
>
> 3. 继续开发
>
> 4. 提交代码
>
>    `git add .`
>
>    `git commit -m 'xx'`
>
>    `git push origin dev`

开发完毕，要上线

> 1. 将dev分支合并到master，进行上线
>
>    `git checkout master`
>
>    `git merge dev`
>
>    `git push origin master`
>
> 2. 把dev分支也推送到远程
>
>    `git checkout dev`
>
>    `git  merge master`
>
>    `git push origin dev`

==注意：==git pull origin dev  等同于  git fetch origin 分支 + git merge origin/分支