### 如何获取git仓库
目前有两种获取git仓库方法：
1. 将尚未版本控制的本地目录转换为git仓库；
2. 从其他服务器```clone```一个已存在的git仓库

##### 在已存在的目录初始化仓库
在windows上
```$ cd 目录地址```

#### 克隆现有的git仓库
``` $ git clone url 自定义命名```

### git的工作流
1. 克隆git仓库为工作目录
2. 在克隆的目录中添加或修改文件。
3. 当他人修改文件，你可以更新资源
4. 在提前交查看修改
5. 提交修改
6. 修改完成后，如有发现错误，可以撤回提交并再次修改提交。
![git工作流](https://github.com/Dec-Ocean/mynote/blob/main/img/git-process.png?raw=true "git工作流程图")

### 检查当前文件状态
我们可以使用```$ git status```命令，查看文件此时正处于什么状态。
当文件出现在```untracked files``的下面，此时意味着文件处于未跟踪状态。
```$ git status```命令的输出十分详细，但用于繁琐。
我们可以使用```$ git status --short```命令或```$ git status -s```命令获得更简洁紧凑的输出。

### 跟踪新文件
当我们需要跟踪一个新文件时，我们可以使用```$ git add```开始跟踪它。
此时再运行```git status```命令，会看到文件已处于被跟踪状态，并进入暂存状态。
出现在```Changes to be committed```的下面，就意味着文件处于已暂存状态。

### 修改已修改的文件
```$ git add```命令是一个多功能的命令：
1. 它可以用于跟踪新文件；
2. 把已跟踪的文件放入暂存区；
3.还能用于合并时把有冲突的文件标记为已解决状态等。
我们可以将```$ git add```命令理解为“精确地把内容添加到下一次提交中”。

### 忽略文件
我们总会有一些无需纳入git的管理的文件，也不希望它们总是出现在未跟踪文件列表中干扰我们。
在这种情况下，我们可以创建一个名为```.gitignore```的文件，列出要忽略的文件的模式。格式如下：
```
{
$ cat .gitignore
*. [oa]
*~ 
}
```

第一行告诉git，这是我们的黑名单列表；
第二行告诉git忽略所有以```.a```或```.o```为后缀的文件。此类存档文件和对象文件都是编译过程中出现的；
第三行告诉git忽略所有名字以波浪符号（~）结尾的文件，许多文本编辑软件都用这样的文件名保存副本。

##### 文件 .gitignore 的格式规范如下：

- 所有空行或者以 # 开头的行都会被 Git 忽略；
- 可以使用标准的 glob 模式匹配，它会递归地应用在整个工作区中；
- 匹配模式可以以（/）开头防止递归；
- 匹配模式可以以（/）结尾指定目录；
- 要忽略指定模式以外的文件或目录，可以在模式前加上叹号（!）取反。

**所谓的glob模式是指shell所使用的简化了的正则表达式。**
- `星号（*）`匹配零个或者多个任意字符；
- `[abc]`匹配任何一个列在方括号中的字符（任选其中一个），如果在`[abc]`中使用短划线分割两个字符，表示所有在这两个字符范围内的都可以匹配(比如`[0-9]`表示可以匹配所有0到9的数字)。
- `问号(?)`只匹配一个任意字符；
- 使用`两个星号（*）`表示匹配任意中间目录，比如`a/**/z`可以匹配`a/z`、`a/b/z`或`a/b/c/z`。

### 查看已暂存和未暂存的修改
`git status`命令的输出并不完全详细，但你想知道具体修改了什么地方时，可以用`git diff`命令。
通常可能会用`git diff`来解决这两个问题：
- 当前做的哪些更新尚未缓存？
- 有哪些更新已缓存并准备好下次提交？
**需要注意，`git diff`本身只显示尚未缓存的改动**
如果需要查看已经缓存起来的变化，`git diff --cached`可以很好的解决你这个需求。

### 提交更新
当暂存区已经准备就绪，我们就可以提交了。但在此之前，请务必确认还有什么已修改或新建的文件还没有`git add`，否则提交的时候将不会记录这些尚未暂存的变化。
所以，每次准备提交前，先用`git status`确认一下，需要提交的文件是不是都已暂存，确认无误后再运行提交命令`git commit`。
通过`git commit -m`可以将提交信息和文件一并发送。

### 跳过使用暂存区域
尽管使用暂存区的方式可以让我们精心准备要提交的细节，但你也觉得这么做有些繁琐吧？不如使用`git commit -a`命令进行提交。
git会自动将所有已经跟踪过的文件暂存并提交，跳过`git add`步骤。
**虽然这个命令很方便，但使用的时候请注意，这个命令有时会将不需要的文件添加到提交中。**

### 移除文件
学会让文件变成已跟踪状态，并让文件进入暂存区，接下来，我们学习将文件从暂存区中移除，并将它从工作目录中删除，使它不会出现在未跟踪文件清单中。
- `git rm`命令可以帮助我们完成这个操作；
- `git rm --cached`命令的功能和`git rm`相似，但它会保留本地文件；
- `git rm`后面也可以使用`glob`模式。

### 移动文件
git并不显示跟踪文件移动操作。如果需要修改一个文件的名字可以使用：
`git mv`命令。

运行`git mv`命令相当于运行了以下三条命令：
```
[
$ mv README.md README
$ git rm README.md
$ git add README
]
```

### 查看提交历史
`git log` 详细说明请看:[https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2]