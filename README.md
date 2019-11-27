# gittest
<strong>这个仓库是用来学习git的一些指令的<strong><br>
#### Git的结构

```
工作区：写代码
        |git add
暂存区：临时存储
        |git commit
本地库：历史版本
```
#### Git和代码托管中心
- 局域网环境下
  Gitlab服务器
- 外网环境下
  Github和码云
#### Git命令行操作
1. git init
初始化本地仓库，会生成.git的隐藏文件
2. 设置签名<br>
   用户名：Tom<br>
    Email地址：XXX@gmail.com<br>
-  项目级别/仓库级别：仅在当前本地库范围内有效<br>
```
git config user.name tom_pro
git config user.email 
```
<br>

-  系统用户级别：登录当前操作系统的用户范围
```
git config --global user.name tom_pro
git config --global user.email XXX@gmail.com
```
3. 添加文件
```
//git add [file name]
//将工作区的“新建/修改”添加到暂存区
 git add .
```
4. 版本库提交
```
//将暂存区的内容提交到本地库
git commit -m "提交的备注" good.txt
```
5. 查看状态
```
git status
```
6. 查看版本历史
```
git log
//格式化
git log --pretty=onelie
git log --oneline
git relflog
```
![image](https://note.youdao.com/yws/public/resource/3be6c2dc5120522e397039ad1efcaeff/xmlnote/0E392FEB864343E791B50764FBC2F1C3/8291)
多屏显示控制方式：<br>
- 空格向下翻页
- b向上翻页
- q退出
7. 前进后退  
-     git reset --hard 【索引值】
8. 删除文件斌找回
-    前提：删除前，文件存在时的状态提交到了本地库
-    操作：git reset --hard[指针位置]<br>
    删除操作已经提交到了本地库：指针位置指向历史记录<br>
    删除操作尚未提交到本地库：指针位置使用HEAD
9. 比较文件差异
-  git dff[文件名]
   将工作区中的文件和暂存区进行比较
- git diff【本地库中历史版本】【文件名】
   将工作区的文件和本地库历史记录比较
-  不带文件名可以比较多个文件
10. 分支操作
-  分支定义
   在版本控制过程中，使用多条线同时推进多个任务
    ![image](https://note.youdao.com/yws/public/resource/3be6c2dc5120522e397039ad1efcaeff/xmlnote/881FE8AEF3BA41D383F4C5A8E14E5C62/8357)
-  创建分支
    git branch【分支名】
-  查看分支
    git branch-v 
-  切换分支
   git checkout 【分支名】
![image](https://note.youdao.com/yws/public/resource/3be6c2dc5120522e397039ad1efcaeff/xmlnote/1AE2B621032F4C249B1DB0108133EAB7/8360)
-  合并分支
    1. 切换到接受修改的分支（被合并，增加新内容）<br>
    git checkout【被合并的分支名】
    2. 执行merge命令<br>
     git merge【有新内容的分支名】
-  解决冲突
    1. 冲突产生的情况
    在master分支修改一个文件的内容，然后add和commit；<br>
    切换到hot_fix分支，在同一行修改同样的文件，然后add和commit；<br>
    这时在hot_fix分支上把master合并回来，或者切换到master合并hot_fix分支都是可以；<br>
    执行git merge master,会产生冲突；
    2. 冲突的解决
   ![image](https://note.youdao.com/yws/public/resource/3be6c2dc5120522e397039ad1efcaeff/xmlnote/2C7D97DF35CA4338B2897909769B38F4/8389)
    vim 编辑冲突的文件;
    然后git add【冲突文件名】；
    最后git commit;==(注意冲突最后的commit不需要呆文件名)==
           
#### github和本地仓库的交互
1. 起别名（将本地仓库和远程仓库进行绑定）
```
git remote add 【别名origin】(github上的项目url地址)
```
2. 推送
-   指令：git push -u orgin master(git push 【别名】 【分支名】)
![image](https://note.youdao.com/yws/public/resource/3be6c2dc5120522e397039ad1efcaeff/xmlnote/4165EEB6F2A247D1AD95D3F9B3D0306F/8472)
3. 克隆
-    如果是其他用户新建的本地仓库克隆，需要先执行git init指令，然后再将git remote add绑定一次；
-    git clone【远程地址】
![image](https://note.youdao.com/yws/public/resource/3be6c2dc5120522e397039ad1efcaeff/xmlnote/AAB561FB32AE4FFFB0926AE72D4B5A42/8448)
-    完整的把远程库下载到本地(.git文件也会被clone下来，这样就不需要执行git init指令)
-    创建origin远程地址别名（执行git remote-v 发现origin的别名也已经创建）
-    初始化本地库
4.  拉取
-  pull = fetch+merge
-  git fetch 【远程地址库别名】【远程分支名】
-  git merge 【远程地址库别名/远程分支名】
-  git pull【远程地址库别名】【远程分支名】
5.  解决冲突
-  如果不是基于Github远程库的最新版本所做的修改，不能推送，必须先拉取
-  拉取下来如果进入冲突状态，则按照“分支冲突解决”

6.注意点和遇到的一些坑<br>
新建了一个分支，在该分支上做了文件的修改，这时候如果没有add和commit就切换到了master分支或者其他分支，再去cat这个修改的文件，会发现master分支上的这个文件也被修改了；
正确的做法是，在新建的分支上要先add和commit，然后切换分支才不会看到修改；这一点是需要注意的<br>


push和pull都是  pull/push -u [别名] + 【分行名】<br>
    
    
linux下按Esc键无法退出的情况
编辑完保存退出的四种方式
1. Esc+：+wq+回车（w是write,q是quit）

2. Esc+：+x+回车（x=wq）

3. Esc+shift+zz

4. Esc+ZZ(在大写开启下)    
    

 

