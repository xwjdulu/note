#命令语句

git add 提交到暂存区 (get add .)

git rm --cached file 撤销暂存区

git commit  提交到本地库

远程库，本地库   pull push clone

.开头文件：隐藏资源

git status 查看状态

Git 执行操作时会自动生成 index.lock 文件，操作结束后会自动删除。这样做的目的是避免同时操作同一个文件夹。

键入git commit 命令后，vscode会弹出一个叫nano的编辑器来要求你填写提交说明（git commit）
弹出的nano编辑器，上面还给了点注释和快捷键参考，其中，”^” 对应 “ctrl” ）

在编辑信息后，想保存并退出nano，按“ctrl+o”。
“ctrl+o”命令，保存对COMMIT_EDITMSG文件的修改并返回，于是进入如下界面，nano确认我们要写入的文件名字：

选择”确认”，因为我们确实是要往COMMIT_EDITMSG文件里写，于是直接回车（enter键)
此时由于我们的修改都已经提交了，所以直接键入“ctrl+x” 离开该界面就可以了，离开界面后，终端提示，commit提交成功

简化这一过程，通过使用” git commit -m “XXXXX” ”命令，就可以跳过nano编辑器直接将git commit附带到提交上，只需要将上述命令中的“XXXXX”环城你想标注的这次提交的commit内容即可

可视化操作：
vscode会在上翻弹出对话框要求你输入此次提交的commit，将git commit 的内容输入即可

git config user.name   git config user.email

***
#软件操作

文件情况：  

新建的文件： 绿色

有改动的文件： 橙色

没有改动的文件： 白色

path配置：

在搜索框中输入 git.path , 找到后点击在 setting.json 中编辑

`
"git.path":"C:/Git/bin/git.exe"
`




