# Lisp and emacs

> 首先感谢这些
[博主:基础用法](http://www.cnblogs.com/sprite_bx/archive/2009/12/07/1618424.html), 
[博主:缓冲管理](http://www.cnblogs.com/robertzml/archive/2010/03/09/1680909.html),
[博主:Org-mode](http://www.cnblogs.com/Open_Source/archive/2011/07/17/2108747.html#sec-1-3),
[博主:任务管理](http://www.cnblogs.com/holbrook/archive/2012/04/14/2447754.html#sec-5),
然后是[Lisp](http://acl.readthedocs.io/en/latest/zhCN/preface-cn.html)中文 

## Project 1 基本操作
- 编写一段普通的文章, 然后保存下来, PS: 写这句话的时候, 我还不知道怎么保存和...退出T_T.
- C 就是Ctrl, M 就是META, 但是Mac上没有META, 所以实际上M是ESC. what the fuck?!!
- 记下以下几个快捷键
  - C - p 光标上移
  - C - n 光标下移
  - C - f 光标右移
  - C - b 光标左移
  - C - l 如果文档超过一屏, 则让光标所在行成为屏幕中间的一行
  - 是的, 以上移动, 一次一个字符
- 以下是更厉害的
  - C - v 下一页
  - M - v 上一页
  - M - f 光标右移, 但是是右移一个词, 嗯..先这么理解: 如果是英语, 是一个单词; 如果是中文, 就直到一个标点符号或者空格;
  - C - a 移动到行首
  - C - e 移动到行尾
  - M - a 移动到上一个句号后面
  - M - e 移动到下一个句号前面, PS: 在markdown里面, 似乎并不好使.
  - M - < 移动到文档头
  - M - > 移动到文档后
  - C - d 删除光标处的一个字符
  - C - DEL / DEL 向左删除一个字符
  - M - d 向右删除一个词
  - M - DEL 向左删除一个词
  - M - SPC 干掉光标附近的空格, 只留以下一个
- 以下是非常危险的操作
  - C - k 向右删除至行尾
  - M - k 向右删除到句号, 句尾
- 希望上面没有写个十几遍, 下面是补救措施(撤销)
  - C - x u = C - _ = C - / 撤销上一步操作, PS. 这句应放在删除前面教!!不能我一个人被坑.
  - 问题来了, 如何Redo ?
- 更高级别的移动光标操作
  - C - u 设定参数给后面的命令, 比如 C - u 8 C - f 表示 光标右移8个字符, C - u 20 C - n
  - 一个比较特殊的案例: C - u 3 C - v 并不是向下翻三页, 而是整个屏幕向上翻三行, 试试? 据说这样比较有意义.
  - C - u [数字] 相当于 M - [数字], 这样就可以少按几个按键
- Yank
  - 先解释以下, Yank是用来存储被删除的内容. 当超过**一个**字符被删除时, 将会被放入到Yank中. 试试? 
  - 了解一些Yank的高级知识: Yank Ring, Ring是一个环状解构, killed的数据被依次放入Ring中, M - y 表示要求换上一个被删除的内容, 试一下.
  - M - y 只能跟在 C - y 后面. 我并不知道, 这个Ring到底有多大, 可以存多少被删除的数据.
  - 似乎已经知道了如何cut then paste 内容了, 虽然这个方法简单粗暴, 但看(shi)上(ji)去(shang)有(fei)点(chang)笨, 那么有没有更好的办法?
  - 答案是**有**! 不过超麻烦! PS. 实际上这并不能作为一个知识点.
  - How to copy and paste? 
    - step 1: M - @ 设置标记
    - step 2: 移动光标
    - M - w 完成范围选择
    - OK, let's try
- 最后一个基本命令: C - g 取消仍未完成的命令

## Project 2 文档操作
- 读档: Emacs术语叫 finding a file
  - C - x C - f 打开文档, 如果打开的文档不存在, 将被创建出来
  - C - x C - s 保存当前文档
  - C - x s 保存所有的文档
  - C - x i 将目标文档插入当前文档
  - M - x dired / C - x d 浏览文档列表
- 视窗: 将窗口划分为多个区域, 每个区域都是一个视窗
  - 分割当前视窗
    - C - x 0 关闭当前视窗
    - C - x 1 关闭除当前视窗以外的任何视窗
    - C - x 2 将当前视窗分割成上下部分
    - C - x 3 将当前视窗分割成左右部分
    - C - x 4 ? 有啥用?
    - C - x 5 ? 没啥用?
  - 多档编辑
    - C - x C - b 打开Buffer List. 这个Buffer List是用来存放emacs打开的文档.
    - C - x b 输入地址, 打开目标buffer
    - C - x o 切换到另一个视窗
    - 如果不知道如何关掉Buffer List, 可以试试 C - x o, C - x 0
    - 更多的信息参见后面的缓冲管理部分
- 保存与退出
  - C - x C - s 表示保存当前文档
  - C - x s 表示保存所有打开的文档
  - C - z 挂起当前emacs实例
  - fg %emacs 可以唤醒最近一次挂起的emacs
  - C - x C - c 表示关闭当前emacs实例
  - emacs每过一段时间都会自动保存一次, auto saving...done.

## Project 3 编辑模式
- 切换模式 M - x
- 普通编辑模式 Fundamental (默认模式)
- 文本编辑模式 Text
- 还有很多其他模式,暂时不关心;

## Project 4 高级功能
- 设置read-only, C - x C - q, 这是一个toggle命令. 意思就是再按一次, 就解除了read-only
- 搜索, 这简直是必须掌握的功能啊!!!啊!!!!
  - C - s 向前(forward)做增量查找;
  - C - r 向后(backward)做增量查找;
  - 此时按C - g, 游标回到原来的位置, 按Enter(回车)则留在当前位置.
  - 是时候试试了.
- 更复杂的查找
  - M - x  search-forward 向下查找
  - M - x  search-backward 向上查找
  - 上面两种方式, 并不具备增量查找的能力, 也不具备让光标回到查询前位置的能力, 目前为止, 我依然认为这个功能很废柴! 讲道理, 难道不废柴?!
  - M - x re-search-forward 用正则表达式来做向下查找, 先试试有没有 M - x re-search-backward, 果然有! 略机智T_T
- 替换
  - M - x replace SPC... PS: SPC 相当于tab, 自动补全命令, 连按两下则有Panel出现.

## Project 5 配置文件
- Emacs的配置文件
  - ~/.emacs 就是配置文件, 如果没有, 自行创建,  这相当于vim的.vimrc;
  - to be continue... PS.现在就像编程? Too young to simple!

## Project 6 缓冲管理


| 按键 | 效果 |
| --- | --- |
| C - x C - b | 打开Buffer Panel |
| RET | 打开选中的Buffer |
| C - u C - x C - b | 排除掉Emacs的缓冲,推荐一般情况下就使用这个查看缓冲. |
| C - x k bufferName | 关闭指定的缓冲 |
| kill-some-buffers | Emacs会逐个询问是否关闭,回答yes/no.'逐个'的意思是,包括emacs的缓冲. |
| clean-buffer-list | 关掉三天都没用过的缓冲 |
| C - x C - q | 切换是否只读 |
| C - u M - g M - g num | 我不想记这个,好难受 |
| rename-buffer | 重命名一个缓冲 |
| rename-uniquely | 重命名当前缓冲,并在名字后加一个数字使其唯一 |
| view-buffer | 只读模式打开一个缓冲,按q退出view模式 |
 

   
   需要特别说的是, CRM列和Buffer列, 先说简单的Buffer列
   Buffer记录了所有缓冲的名字,其中被*name*的缓冲是Emacs的,最好不要改它们.
   接着说CRM.CRM展开的意思就是Current/ReadOnly/Modify,分别标识当前(.),只读(%)和已修改(*)


   更多buffer-menu的操作


| 按键 | 效果 | 备注 |
| --- | --- | --- |
| n | 下一项 | |
| p | 上一项 | |
| d或k | 标记删除 | 需要通过x执行 |
| C - d | 标记删除 | 需要通过x执行 |
| s | 标记保存 | 需要通过x执行 |
| x | 执行删除或保存 | |
| u | 取消标记,并移动到下一项 | |
| backspace | 取消标记,并移动到上一项 | |
| f或RET | 打开缓冲 | |
| o | 打开缓冲,并选中视窗 | |
| C - o | 打开缓冲,并不选中视窗 | |
| m | 标记缓冲要在新视窗显示 | |
| v | 显示标记的缓冲 | |
| q | 退出Buffer Menu | |


## Project 7 Org-mode

   > 参考first.org

### 标题
 
\*表示标题,且\*数量表示级别.数量越多级别越低.最多8级.

#### 移动 

| 按键 | 效果 |
| --- | --- |
| C - c C - n | 下一个标题 |
| C - c C - p | 上一个标题 |
| C - c C - f | 下一个同级别标题 |
| C - c C - b | 上一个同级别标题 |
| C - c C - u | 回到上级标题 |

#### 结构编辑

| 按键 | 效果 |
| --- | --- |
| M - RET | 插入同级别标题 |
| M - S - RET | 插入一个同级别TODO项 |
| TAB | 如果还没有文字,自动调整到合适的级别;如果有文字,则进行折叠/展开 |
| M - Left/Right | 当前项提升/降低级别 |
| M - Up/Down | 当前项与同级项交换位置 |
| C - c C -c | 给标题添加标签 |
| C - c C - w | 将当前项传送到另一个文件中 |
| C - x n s/w | 将视域局限到当前项/放宽视域 |

#### 稀疏树

| 按键 | 效果 |
| --- | --- |
| C - c / | 打开命令 |
| C - c / r | 利用正则筛选目标并高亮显示 |
| C - c C - c | 取消高亮 |

### 文本列表

> Org能识别有序列表,无序列表,描述列表

无序列表以 - + * 开头


有序列表以 1. 1) 开头


描述列表用 :: 将项和描述分开


任务列表以 [ ] 开头, 在任意位置插入[/][%]可以跟踪任务完成情况


| 按键 | 效果 |
| --- | --- |
| S + Left/Right | 切换列表类型 |
| M + Left/Right | 提升/降低等级 |
| M + Up/Down | 列表项调整顺序 |
| C - c C - c | 选中或取消选中任务列表项 |
| S + Up/Down | 上一项/下一项 |
| C - c C - t | 将标题变成TODO |


更有意思的事情是,可以自己定义任务的状态,如下局部定义

`#+SEQ_TODO: TODO(T!) DONE(D!/@)`

全局定义则将以下代码添加到.emacs中

```
(setq org-todo-keywords
    '((sequence "REPORT(r)" "BUG(b)" "KNOWNCAUSE(k)" "|" "FIXED(f)")
          (sequence "TODO(T!)" "|" "DONE(D@)3" "CANCELED(C@/!)")
	       )) 
```

- 序列可以定义多个
- 状态之间用空格分隔
- `|`状态分组
- 状态格式为`<状态名>([快捷键][@][/!])`
  - `()`中是附加项
  - `@`表示切换到该状态需要文字说明
  - `!`表示切换到该状态会自动添加时间戳
  - 注意,@和!同时使用需要用`/`分隔


| 按键 | 效果 |
| --- | --- |
| S + Up/Down | 改变TODO标题的优先级, 共三级A,B,C |
| C - c , | 设置优先级 |


**注意：**
当改变子任务状态时，只更新上一级任务的完成情况，不可级联。
即使所有的子任务都完成，也只是标记上一级任务的完成情况为100%，而不能自动更新上级任务的完成状态。如果需要自动设定为完成，可以在.emacs中增加如下配置：

```
	(defun org-summary-todo (n-done n-not-done)
	      "Switch entry to DONE when all subentries are done, to TODO otherwise."
	            (let (org-log-done org-log-states)   ; turn off logging
		            (org-todo (if (= n-not-done 0) "DONE" "TODO"))))

    (add-hook 'org-after-todo-statistics-hook 'org-summary-todo)
```

- 任务时间计划

| 按键 | 效果 | 备注 |
| --- | --- |
| C - c ! | 输入一个[时间] |
| S - Left/Right | 调整天 | 光标需停在时间戳范围内 |
| S - Up/Down | 调整光标所在日期部分 | 比如:年,月,日,星期 |
| C - c > | 查看日历 |
| C - c < | 输入yige <时间> |
| C - c C - y | 计算时间范围间隔天数 |


*TIPS*: 用 - 连接两个<时间>, 可以得到一个时间范围

- 计划时间 和 截止时间

| 按键 | 效果 | 备注 |
| --- | --- | --- |
| C - c C - s | 给标题设置计划时间 |
| C - c C - d | 给标题设置截止时间 |

- 全局任务清单

添加如下代码到.emacs

```
(global-set-key "\C-cl" 'org-store-link)
(global-set-key "\C-cc" 'org-capture)
(global-set-key "\C-ca" 'org-agenda)
(global-set-key "\C-cb" 'org-iswitchb)
```

如果配置上述代码, 将会有以下按键效果

| 按键 | 效果 | 备注 |
| --- | --- | --- |
| C - c a t | 进入全局TODO列表 | 全局TODO列表中列出所有全局文件中的未完成任务 |
| C - c a a | 进入全局计划列表 |  *还不知道是什么* |
| C - c b | 按org文件名打开配置在org全局列表中的org文件 |
| C - c c | *不知道做什么的* |
| C - c l | 存储链接 |  执行org-store-link |
| C - c C - l | 插入链接 | 执行org-insert-link |
| C - c C - o | 打开链接 | 执行org-open-at-point |
| C - c % | 记录内部链接地址 |
| C - c & | 跳转到已记录的内部地址 |


所谓内部链接, 就是如下这样的:

```
定义锚点 #<<my-anchor>>
[[my-anchor][内部链接]]
```


还有一种特殊的内部链接, 只是多了*fn:*的前缀:

```
定义脚注 [fn:my-anchor]
[[fn:my-anchor][脚注1]]
```


另外还有一些按键

| 按键 | 效果 |
| --- | --- |
| C - c [ | 在org文件中, 可以将任务标题添加到全局TOOO列表 |
| C - c ] | 在org文件中, 可以将任务标题移出全局TODO列表 |


*TIPS*: 在全局TODO列表时, t 可以改变任务状态, RET 可到达任务所属源文件

