Vim学习笔记
====================


## 技巧


### 字符操作

#### 基础
* i  进入Insert模式
* o  进入Insert模式并换行
* r  replace 替换
* a  append 追加
* p  黏贴于光标后
* P  黏贴于光标前
* visual 模式下面的字符串选择

#### 进阶
* ]p 自動indent的黏貼
* :n1,n2 m n3     移动n1-n2行(包括n1,n2)到n3行之下；
* :n1,n2 co n3    复制n1-n2行(包括n1,n2)到n3行之下；
* :n1,n2 d        删除n1-n2行(包括n1,n2)行

### 光标移动

#### 基础
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

#### 进阶

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

### 文件操作

#### 基础
* vim -o file….  水平分割打开几个文件
* vim -O file…  垂直分割打开几个文件
* :new filename 在新窗口打开查看文件
* :vert new filename 水平分割打开新窗口
* :tab new 在新tab创建文件

### buffer的操作

####基础
* :ls 或者 :buffers 查看buffer列表
* :vert sb N   在垂直窗口打开列表
* :bfirst 去到第一个buffer
* :bn  next buffer
* :bp  prev buffer
* :e <filename> will just open into a new buffer. 

## 窗口管理

概念：

* A buffer is the in-memory text of a file.
* A window is a viewport on a buffer.
* A tab page is a collection of windows.

### window
#### 基础

* `Ctrl-W n` 创建一个水平新窗口，新建文件  等同于 :new   而:vne则是建立一个垂直分割的窗口
* `Ctrl-W s` 创建水平分割窗口，编辑当前Buffer   :sp
* `Ctrl-W v`  创建垂直分割窗口，编辑当前Buffer
* `Ctrl-W q`  关闭一个分割窗口
* `Ctrl-W r`  向右移动窗口*
* `Ctrl-W T`  移动窗口到新Tab
* `Ctrl-W`

#### 进阶
* `Ctrl-W r`  向下/向右移动窗口
* `Ctrl-W R` 向上/向左移动窗口
* `Ctrl-W K` 移动到最顶端，宽度满屏
* `Ctrl-W J` 移动到最低，宽度满屏   Ctrl-W H 和 Ctrl-W L 与之同理，分别移动到最左最右 
* `Ctrl-W =` 均分窗口
* `Ctrl-W t Ctrl-W K`    将两个垂直分割变为水平分割 
* `Ctrl-W t Ctrl-W H`    将两个水平分割变为垂直分割
* `Ctrl-W Shift-T`    将窗口移动到tab中 
* `Ctrl-W t` makes the first (topleft) window current Ctrl-W K moves the current window to full-width at the very top 
* `Ctrl-W H` moves the current window to full-height at far left
* `Ctrl - W R`  向右移动

### tab
#### 基础
* `gt` 向左移动
* `gT` 向右移动
* `ngt`  移动到第n个

#### 进阶
* :tabm n 移动当前tab的位置，如果要将tab的位置移动到最后，可以输一个足够大的值 tabm 99 就可以移动到最后了 tabm 0移动到最前
* :tabonly 关闭其他窗口


## [内容查找替换](http://vim.wikia.com/wiki/Searching%20)

### 文件内查找替换
[addr]s/源字符串/目的字符串/[option]

[addr] 表示检索范围，省略时表示当前行。如：“1，20” ：表示从第1行到20行；“%” ：表示整个文件，同“1,$”；“. ,$” ：从当前行到文件尾；
[option] : 表示操作类型   如：g 表示全局替换; c 表示进行确认 p 表示替代结果逐行显示（Ctrl + L恢复屏幕）； 


`:%s/foo/bar/g` 将整个文件中的foo替换为bar，不需要确认

###跨文件文件查找

使用：`vimgrep  /{pattern}/[g][j]   files`

例如:查找目录pulibc/js下的文件中是否有 function1
`vimgrep  /function1/  ./public/js/**/*.js`

:copen 打开quickfix

参考
1. [tab使用秘籍](http://vim.wikia.com/wiki/Quick_tips_for_using_tab_pages)

## 参见问题

###如何定义快捷键

```:map <F5> i{e<Esc>a}<Esc>```

i{将插入字符{，然后使用Esc退回到命令状态；接着用e移到单词结尾，a}增加字符}，最后退至命令状态。在执行以上命令之后，光标定位在一个单词上（例如amount），按下F5键，这时字符就会变成{amount}的形式。

使用以下命令，可以在Normal Mode和Visual/Select Mode下，利用Tab键和Shift-Tab键来缩进文本：

```
nmap <tab> V>
nmap <s-tab> V<
vmap <tab> >gv
vmap <s-tab> <gv
```

使用以下命令，指定F10键来新建标签页：

```
:map <F10> <Esc>:tabnew<CR>
```

* :nmap - Display normal mode maps
* :imap - Display insert mode maps
* :vmap - Display visual and select mode maps
* :smap - Display select mode maps
* :xmap - Display visual mode maps
* :cmap - Display command-line mode maps
* :omap - Display operator pending mode maps
参考: (给vim自定义快捷键)[http://www.pythonclub.org/linux/vim/map]


## 組合技

### 常用
* `$ a` $  跳到行尾，a 在最后位置开始输入
* `gg“+yG`    将文件内容复制到剪贴版     gg跳到第一行  “+ 选择存放的寄存器  yG复制所有行数
* visual模式下
    * `a(   a)   ab`  选择括号和括号里面的内容   ( content )
    * `i(   i)   ib` 选择括号里面的内容       ( content ) 
    * `‘  “    [`  这些都可以与上同理 例如  i’ 选择单引号里面的内容，a[ 选择中括号和中括号里面的内容
* ciw 改变单词

## 插件列表


* vim-scripts / Visual-Mark  https://github.com/vim-scripts/Visual-Mark/      
* kien / ctrlp.vim   https://github.com/kien/ctrlp.vim  轻量级的文件切换工具 
* SirVer / ultisnips  https://github.com/SirVer/ultisnips    神级插件 http://fueledbylemons.com/blog/2011/07/27/why-ultisnips/  
* terryma / vim-multiple-cursors   实现Sublime的Ctrl-D功能 多行同时编辑
* tpope / vim-unimpaired   可以方便的执行:lprev ( [l ), :lne( ]l )的命令，还有可以实现移动行  [e ]e 类似于Sublime的 移动行 
* tpope/commentary.vim  注释插件
* tabular 方便文本对齐 https://github.com/godlygeek/tabular
* Ack 搜索关键词 https://github.com/mileszs/ack.vim 
* mru https://github.com/yegappan/mru 最近打开的文件

## 资料
1. [What is your most productive shortcut with Vim?](http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim/1220118220118)
