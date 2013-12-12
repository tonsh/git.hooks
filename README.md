# Git Hooks

## Features
* 代码提交前对缓存区中的 Python 文件进行自动语法检查(pyflakes)、 代码规范检查(pep8)、 单元测试（仅运行缓存区中的测试文件）。
* 代码推送前运行完整的单元测试。
* 代码推送成功后会重启服务器等。

## pre-commit

提交代码前，实现了自动语法检查，代码规范，单元测试。

如果提交的代码存在语法错误，是必然不会被提交的。pre-commit 会将错误信息打印出来并拒绝提交；若不是严重的语法错误，而是有一些代码规范的问题，pre-commit 会询问提交者是否停止提交，修正错误；为了代码风格一致，这里建议进行修正。
 
如果本次提交中有修改或新加单元测试文件，pre-commit 会运行这些被修改的测试文件的单元测试，如果不能顺利通过，提交动作也会被拒绝。

#### Requirement

* **pyflakes**

	pip install pyflakes

* **pep8**

    pip intall pep8
   
* **nosetests**


## pre-receive
向服务器推送代码前，运行全部的单元测试。
该脚本是放在服务端的。

## post-receive
推送完成后，进行编译（coffeescript, less 等），重启服务器等。

### Installing

将钩子脚本添加到项目目录下的 .git/hooks/ 目录下。并确认脚本有可执行权限。