Vim学习笔记
====================


## 技巧


###字符操作

###基础
* i  进入Insert模式
* o  进入Insert模式并换行
* r  replace 替换
* a  append 追加
* p  黏贴于光标后
* P  黏贴于光标前
* visual 模式下面的字符串选择
####进阶
* ]p 自動indent的黏貼
* :n1,n2 m n3     移动n1-n2行(包括n1,n2)到n3行之下；
* :n1,n2 co n3    复制n1-n2行(包括n1,n2)到n3行之下；
* :n1,n2 d        删除n1-n2行(包括n1,n2)行

###光标移动

####基础
* gg 首行
* G  尾行
* 80% 文件80%处
* ^ 行首
* $ 行尾
* gi 回到最后一次编辑的位置
* % 在括号的头尾来回切换
* e 单词尾部
* w 下一个单词
* b 上一个单词
* fx/Fx 向前/向后 移动到任意字符x处
* nG 跳到第n行
* Ctrl-f  前进一页
* Ctrl-b  后退一页
* * 移動到下一個與當前單詞一樣的單詞
* # 移動到下一個與當前單詞一樣的單詞

####进阶

* H 跳到窗口顶部
* M 跳到窗口中央
* L 跳到窗口底部
* zz - move current line to the middle of the screen
* zt - move current line to the top of the screen
* zb - move current line to the bottom of the screen
* ma 标记当前行
* ‘a 跳到标记a的行
* ‘’ (两个单引号)  回到上一次跳转位置
* visual 模式下  < > 是缩进的控制
* 大小写改变
  * ~ 单个字符大小写切换
  * g~ (大小写切换) ，gu (变小写), gU (变大写)  通过movement（即上下左右）来控制 例如：g~上, 可以把当前行和上一行变为大(小)写
  * gUU(当前行变大写) g~~(当前行大小写切换) guu （当前行变小写）
  * 可以跟上w, b,$, ^等来自由发挥， 例如  gu3w  将前面3个单词变小写  同理的还有 gu3b  gU3w  g~$   g~^等等



## 资料
1. [What is your most productive shortcut with Vim?](http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim/1220118#1220118)
