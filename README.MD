# Lisp and emacs

首先感谢 http://www.cnblogs.com/sprite_bx/archive/2009/12/07/1618424.html
Lisp中文 http://acl.readthedocs.io/en/latest/zhCN/preface-cn.html

## Project 1 基本操作
- 编写一段普通的文章, 然后保存下来, PS: 写这句话的时候, 我还不知道怎么保存和...退出T_T.
- C 就是Ctrl, M 就是META, 但是Mac上没有META, 所以实际上M是ESC. what the fuck?!!
- 记下以下几个快捷键
  - C + p 光标上移
  - C + n 光标下移
  - C + f 光标右移
  - C + b 光标左移
  - C + l 如果文档超过一屏, 则让光标所在行成为屏幕中间的一行
  - 是的, 以上移动, 一次一个字符
- 以下是更厉害的
  - C + v 下一页
  - M + v 上一页
  - M + f 光标右移, 但是是右移一个词, 嗯..先这么理解: 如果是英语, 是一个单词; 如果是中文, 就直到一个标点符号或者空格;
  - C + a 移动到行首
  - C + e 移动到行尾
  - M + a 移动到上一个句号后面
  - M + e 移动到下一个句号前面, PS: 在markdown里面, 似乎并不好使.
  - M + < 移动到文档头
  - M + > 移动到文档后
  - C + d 删除光标处的一个字符
  - C + DEL / DEL 向左删除一个字符
  - M + d 向右删除一个词
  - M + DEL 向左删除一个词
- 以下是非常危险的操作
  - C + k 向右删除至行尾
  - M + k 向右删除到句号, 句尾
- 希望上面没有写个十几遍, 下面是补救措施(撤销)
  - C + x u = C + _ = C + / 撤销上一步操作, PS. 这句应放在删除前面教!!不能我一个人被坑.
  - 问题来了, 如何Redo ?
- 更高级别的移动光标操作
  - C + u 设定参数给后面的命令, 比如 C + u 8 C + f 表示 光标右移8个字符, C + u 20 C + n
  - 一个比较特殊的案例: C + u 3 C + v 并不是向下翻三页, 而是整个屏幕向上翻三行, 试试? 据说这样比较有意义.
  - C + u [数字] 相当于 M + [数字], 这样就可以少按几个按键
- Yank
  - 先解释以下, Yank是用来存储被删除的内容. 当超过**一个**字符被删除时, 将会被放入到Yank中. 试试? 
  - 了解一些Yank的高级知识: Yank Ring, Ring是一个环状解构, killed的数据被依次放入Ring中, M + y 表示要求换上一个被删除的内容, 试一下.
  - M + y 只能跟在 C + y 后面. 我并不知道, 这个Ring到底有多大, 可以存多少被删除的数据.
  - 似乎已经知道了如何cut then paste 内容了, 虽然这个方法简单粗暴, 但看(shi)上(ji)去(shang)有(fei)点(chang)笨, 那么有没有更好的办法?
  - 答案是**有**! 不过超麻烦! PS. 实际上这并不能作为一个知识点.
  - How to copy and paste? 
    - step 1: M + @ 设置标记
    - step 2: 移动光标
    - M + w 完成范围选择
    - OK, let's try
- 最后一个基本命令: C + g 取消仍未完成的命令

## Project 2 文档操作
- 读档: Emacs术语叫 finding a file
  - C + x C + f 打开文档
  - C + x C + s 保存当前文档
  - C + x s 保存所有的文档
  - C + x i 将目标文档插入当前文档
- 视窗: 将窗口划分为多个区域, 每个区域都是一个视窗
  - 分割当前视窗
    - C + x 0 关闭当前视窗
    - C + x 1 关闭除当前视窗以外的任何视窗
    - C + x 2 将当前视窗分割成上下部分
    - C + x 3 将当前视窗分割成左右部分
    - C + x 4 ? 有啥用?
    - C + x 5 ? 没啥用?
  - 多档编辑
    - C + x C + b 打开Buffer List. 这个Buffer List是用来存放emacs打开的文档.
    - C + x b 输入地址, 打开目标buffer
    - C + x o 切换到另一个视窗
    - 如果不知道如何关掉Buffer List, 可以试试 C + x o, C + x 0
- 保存与退出
  - C + x C + s 表示保存当前文档
  - C + x s 表示保存所有打开的文档
  - C + z 挂起当前emacs实例
  - fg %emacs 可以唤醒最近一次挂起的emacs
  - C + x C + c 表示关闭当前emacs实例
  - emacs每过一段时间都会自动保存一次, auto saving...done.

## Project 3 编辑模式
- 切换模式 M + x
- 普通编辑模式 Fundamental (默认模式)
- 文本编辑模式 Text
- 还有很多其他模式,暂时不关心;
- to be continue...
