# **git进行版本控制步骤**

## 一 基础操作

* 进入要管理的文件夹

* 执行初始化命令


```git
git init
```

* 管理目录下的文件状态[^1]


```git
git status
```

* 管理指定的文件


```git
git add 文件名
git add .
```

* 生成版本


```git
git commit -m '描述信息'
```

* 查看版本记录

```git
git log
```

* 回滚至之前版本

```git
git log
git reset --hard 版本号
```

* 回滚至之后版本

```git
git reflog
git reset --hard 版本号
```

> ### 小总结
>
> ```
> git init
> git add
> git commit
> git log
> git reflog
> git reset --hard 版本号
> ```

![image-20210517201126342](C:\Users\nero\Desktop\Git实战\image-20210517201126342.png)

[^1]: 新增的文件和修改过的文件都是红色

## 二 分支命令总结

![image-20210517201207505](C:\Users\nero\Desktop\Git实战\image-20210517201207505.png)

* 查看分支

```
git branch
```

* 创建分支

```
git branch 分支名称
```

* 切换分支

```
git checkout 分支名称
```

* 分支合并(可能产生冲突)[^2]

```
git merge 要合并的分支
```

* 删除分支

```
git branch -d 分支名称
```

![image-20210517201441704](C:\Users\nero\Desktop\Git实战\image-20210517201441704.png)

[^2]: 切换分支再合并

## 三 github

![image-20210517201714241](C:\Users\nero\Desktop\Git实战\image-20210517201714241.png)

### 开始使用github

* 创建远程仓库

![image-20210517201947789](C:\Users\nero\Desktop\Git实战\image-20210517201947789.png)

```
1. 给远程仓库起别名
	git remote add 别名 远程仓库地址
2. 查看当前仓库地址
	git remote -v
3. 向远程推送代码
	git push -u origin 分支
4. 修改仓库别名
	git remote rm origin
	git remote add origin2
```

![image-20210517210245774](C:\Users\nero\Desktop\Git实战\image-20210517210245774.png)

###### 下载代码(初次在公司新电脑下载代码)

```
1. 克隆远程仓库代码
	git clone 仓库地址(自动进行git remote add origin)
2. 切换分支
	git checkout 分支
```

在公司下载完代码后,继续开发

```
1. 切换到dev分支进行开发
	git checkout dev
2. 把master分支合并到dev(仅一次)
	git merge master
3. 修改代码
4. 提交代码
	git add
	git commit -m 'xx'
	git push -u origin dev  //-u:默认push向origin提交dev,可省略
	git push origin dev
```

###### 下班回家后继续写代码

 ```
 1. 切换到dev分支进行开发
 	git checkout dev
 2. 拉代码
 	git pull origin dev
 3. 继续开发
 4. 提交代码
 	git add .
 	git commit -m 'xx'
 	git push origin dev
 ```

###### 到公司继续开发

```
1. 切换到dev分支进行开发
	git checkout dev
2. 拉最新代码
	git pull origin dev
3. 继续开发
4. 提交代码
	git add .
	git commit -m 'xx'
	git push origin dev
```

开发完毕上线

```
1. 将dev分支合并到master,进行上线
	git checkout master
	git merge dev
	git push origin master
2. 把dev分支也推送到远程
	git checkout dev
	dit merge master
	git push origin dev
```



>##### 关于pull
>
>pull = fetch + merge
>
>```
>git pull origin dev = git fetch origin dev + git merge origin/dev
>```

## rebase(变基)的作用

rebase可以保持提交记录简洁

当有多次提交记录,可合并不重要的部分,如

![image-20210521092234189](C:\Users\nero\AppData\Roaming\Typora\typora-user-images\image-20210521092234189.png)

```
git rebase -i 版本号(C?)
合并当前(C4)至C?的版本
例如
git rebase -i c5577ffcab4f67645fa1b6a654825fea72aed8aa
合并C4到c5577ffcab4f67645fa1b6a654825fea72aed8aa(C2)的版本
```

