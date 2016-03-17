---
layout:     post
title:      "如何用 OS X 的 Xcode 写 C 语言程序"
subtitle:   "OS X，Xcode，C语言"
date:       2016-03-01
author:     "Francis Soung"
header-img: "img/post-bg-os-metro.jpg"
tags:
    - 编程
    - Xcode
    - C语言
    - OS X
    
---


如果你在 Windows 习惯使用 Visual C++ 或 Dev-C++ 的话，到了 Mac OS X 可能会突然不知道要怎么写程序，尤其当你已经用 Visual C++ 的 Debugger 用得很上手的话。

要对自己重新进修了，最近上的课充满了 C programming，虽然大学学过，但是那时候并没有钱买Mac，现在有机会了，我也稍微摸懂了 Xcode 的若干功能，至少我可以拿它来写 C 语言的程序了，就像在 Windows 使用 Visual C++ 那样。

如果这篇只是要教你怎么按 Compile 的话，那我就是来骗阅读数的了，因此这篇的内容还包括 **怎么使用 Xcode 的 Debugger** 。

### 安裝 Xcode

Xcode 是在 OS X 上面写 C 语言程序最简单的方式。首先是去 Mac App Store 下载安装 Xcode ，网址： [https://itunes.apple.com/cn/app/xcode/id497799835?mt=12](https://itunes.apple.com/cn/app/xcode/id497799835?mt=12) 。免费的，只是要装很久。安装完成后，可以在 Launch Pad 里面找到 Xcode ，按一下开启。如果找不到的话，可以在 Spotlight （屏幕右上角的放大镜）里面搜寻 "Xcode" ，也可以找到。

第一次打开 Xcode 你会看到 Welcome to Xcode 的画面，做为第一次尝试，请先按下 **Create a new Xcode Project** 。

![XMH0eBTHTtCbw0brEgdY_Screen Shot 2013-12-01 at 15.27.42.png][1]

Welcome to Xcode 這个界面若以后不想看到，可以取消勾选 **Show this window when Xcode launches** 來永久关闭，以后若要创建新项目，可以按下功能表的 **File → New → Project** ... 。

### 新建 C 语言项目

刚刚说按下 **「Create a new Xcode Project」**，接着会跳出一个视窗，问你要创建什么项目。对于一般 **C** 程序来说，它被归类在 **OS X** 的命令列工具里面，所以，在左侧选 **OS X**里面的 **Application** ，然后在右边选 Command Line Tool 。

![7oyl8cvvSWKa56Lob40B_Screen Shot 2013-12-01 at 15.41.16.png][2]

接着会要你输入项目名称，**Organization Name** 写你的名字就行， **Company Identifier** 我不知道是做什么的（我不是专门写 OS X 程序的），但并不会影响接下来的操作，所以像我这样填一个看起来像样的（？）就行。最下面的 Type 可以选 C 或 C++ ，还有其他 Objective-C-based Frameworks，这里我直接选 C 。

![OeFtlK2TRugmCdMiXVKg_Screen Shot 2013-12-01 at 15.42.58.png][3]

最后按下 Next ，会要你找一个地方放这个项目，你就找个地方放就行了。

### 认识 Xcode IDE

Xcode IDE 的界面一打开跟 **Visual Studio**、 **Dev-C++** 都不一样，从 Windows 来的人可能会不太习惯，不过不要紧，只要认识几个东西就好了。

但在开始认识之前，请先到 **Xcode → Preferences...** 里面的 Behaviors ，选 **Running → Starts** ，把 **Show debugger** 打开，并且把 Debug Area 打开，在 **View → Debug Area → Show Debug Area** 。这个预设没开，但接下来会用到，非常重要，所以先打开。

![NqjAUPYTiiB6d4qg0IXv_Screen Shot 2013-12-01 at 16.47.13.png][4]

接下来来认识一下 Xcode Project 视窗的基本配置：

![eSqQS2rtTqC38sou72Ul_Screen Shot 2013-12-01 at 15.54.26.png][5]

请先认识：

* **「执行」按钮 (Run)** ，长得像音乐软件的 **Play** ，按下去就是执行程序程序

* **「停止」按钮 (Stop)** ，长得像音乐软件的 **Stop** ，在程序执行的时候可以强制停止

* **「状态列」** ，在最上方，会出现的状态像是编译或执行的成功与否

* **「左侧栏」** ，现在是显示档案列表（有其他列表可以切换）

* **「主要工作区」** ，现在里面是看不懂的东西，等下会切换到程序码编辑

* **「除错区」** ，让你方便对程序码除错，我会特别讲这一个区域。

### 第一次执行程序

写程序除了撰写程序码本身，最重要的就是要跑程序来看结果。刚刚介绍了**「执行」**按钮，看起来可以按它来执行程序，那么就按按看吧。按下去之后，你会看到状态列的信息有所改变，提示 **Building** 、 **Build Success** 、**Running** 等等，最后，你会在 Debug Area 的右边看到这个：

![C3XtPoWbT6mkeePOvNPg_Screen Shot 2013-12-01 at 16.03.27.png][6]

嗯，程序可以执行，可以看到输出了。

### 第一次修改程序

但是到现在还没看到程序码，刚刚说了左侧栏是切换到**「档案列表」**，也就是说档案藏在里面，请找一下** main.c** ，按一下可以打开，主要工作区会变成程序码：

![sEU0GDnJSNSDiiIygHVg_Screen Shot 2013-12-01 at 16.07.13.png][7]

这个程序码你应该很熟悉，就是普通的 C 语言 Hello World 而已。

### 自动完成

接下来请试试看修改程序。假如我想要改成印出 10 次 Hello World 的内容，想必你会在 `// insert code here` 这边加 for loop：

```
int i;

for (i = 0; i < 10; i++) {

  printf("Hello, World\n");

}
```

你打到一半的时候应该会出现这样子的东西：

![gI4TrStRjCKpsqOM6ZYw_Screen Shot 2013-12-01 at 16.09.45.png][8]

这个功能叫做 「自动完成」 (Auto Complete) ，是 Xcode 好用的功能之一，如果你从 **Visual Studio** 过来应该不陌生，就是打到一半，Xcode 会自动提示你可以写什么程序码，并且按下 Tab 就可以自动跳到圆框来打字。你可以试试看，按 Tab 来切换，然后按 Enter 来确认。

自动完成其实无所不在，除了可以自动展开 **Syntax** 之外，还可以展开变量名称、function 名称（统称 identifiers）、提示有哪些 .h 档可以 **include** 、提示 **struct** 的结构。展开 identifers 的例子像是，你想要用 **fputs** ，打 **fp** ，它会自动出现所有 **fp** 开头的函式（因为有 **include stdio.h** ，所以抓得到），按键盘的上下键可以选择，除此之外，还会在右侧栏出现简单的说明。

如果你按 More 的话，还会出现完整的说明文档，这样子就不需要上网查文件了。

![LmAI0OiKQ0eyFFsTWESI_Screen Shot 2013-12-01 at 16.28.08.png][9]

再提一个秘诀，想要手动 **trigger** 自动完成的话，可以按 **Esc** 。例如我先声明了 var1, var2, var3 ，想要对其中一个指定某值，打到一半只有 **var** 就跑到别行，再回来的话，可以在 **var** 的后方按 **Esc** ，就会跳出自动完成：

![YuMTYksOQZ2PDtlkIB9M_Screen Shot 2013-12-01 at 16.34.47.png][10]

附带一提，大小写随便打，它也认得出来。

你可以随便试，你应该会感受到**「他好像很聪明的样子」**。

### 自动错误提示

我改好了，结果 oops ，好像忘记什么东西？

![ao21Ze16Q0u5KhLD9Jfi_Screen Shot 2013-12-01 at 16.12.08.png][11]

老师有教过变量要声明！

程序写错，不用到编译才知道， Xcode 会一直自动编译，检查你程序码是否可以编译通过，并且自动 **标示错误** ，如果你按下行号旁边的红色惊叹号，它会告诉你错在哪：

![arO3fNDURbOtN2k9nmhR_Screen Shot 2013-12-01 at 16.14.16 (1).png][12]

对，忘记声明了，补起来之后，这个错误信息就会消失了。

错误信息除了程序写错无法编译之外，还会有编译器来的警告，例如有个变量声明了但没使用：

![ZsanqbuyRLmhb7e7dm2c_Screen Shot 2013-12-01 at 16.18.11.png][13]


如何，很方便吧？

执行程序与输入资料

现在再来 **Run** 一遍，这次不要动鼠标了，请按键盘上的 **Command + R** ，一样会跑「执行」：

![1Iz1SmUHRKWqL8R1HNdn_Screen Shot 2013-12-01 at 16.16.54.png][14]

如果是从 **Visual Studio** 或**Dev-C++** 过来的，你可能会觉得奇怪，为什么不是熟悉的黑底白字画面？其实 Xcode 在执行的时候，并不是开一个新的终端机程序，而是直接在自己的 **Console** 里面输入输出，我猜测这理由是因为 **Xcode** 是以 GUI 应用程序为主要导向，所以 **Console** 简略就好，并且因为 OS X 是一种 **UNIX** 系统，天生就有输入输出转向，可以直接接到 Xcode 里面也很自然（这个在系统程序的课会教）。话说回来 Eclipse 好像也是长这样。

不过，预设它并不会在执行的时候自动打开 **Console**，你必须手动开启，所以一开始我才会请你先打开 Debug Area 。

接下来试着执行一个具备输入输出的简单程序，输入整数 n ，输出 n 次 `"Hello, World!\n"`。

```
int main(int argc, const char * argv[])
{
  int i, n;
  
  if (fscanf(stdin, "%d", &n) == 1) {
    for (i = 0; i < n; i++) {
      printf("Hello, World!\n");
    }
  }
  
  return 0;
}
```

按下 Run ，然后在 Console 里面输入 3 ，它就会输入整数 n = 3 ，并且印出 3 次 `Hello, World!` ，跟我们想要的行为一致。

![1mU3yqGNSXSNj7MdHlEV_Screen Shot 2013-12-01 at 16.54.50.png][15]

如果你执行到一半想把程序关掉，只要按下 **Stop** 就行了。

### 使用 Debugger

跟 Visual Studio 一样，专业的 IDE 一定要有完美的 Debugger 整合，而 Xcode 当然也有，这对于我这种不熟悉命令列式 debugging 的人来说是相当棒的功能。 一般的命令列 debugger 要自己下断点（告诉它在第几行）、自己下指令，但有了 Xcode ，你只要动鼠标就行了。

以下以一个简单的小程序做示例：

```
#include <stdio.h>

/* global variables */
int i_am_a_global_variable = 999;

/* functions */

void another_function (int* a)
{
  (*a)++;
  i_am_a_global_variable += *a;
  return;
}

int some_function (int a)
{
  int some_local_var = a;
  printf("some_local_var has been changed to %d\n", some_local_var);
  another_function(&some_local_var);
  printf("some_local_var has been changed to %d\n", some_local_var);
  return 0;
}

int main (void)
{
  int number;
  printf ("enter number:");

  if (fscanf(stdin, "%d", &number) == 1) {
    some_function(number);
    printf("You’ve entered %d\n", number);
  } else {
    printf("No number entered. Bye.\n");
  }
  
  return 0;
}
```

断点的定义是 **「在执行这一行之前先回到 debugger」** ，也就是说如果你把断点设在第 12 行，那么它会在执行第 12 行之前暂停程序执行，进入 debugger。

设断点的方法很简单，在行号上 **按一下鼠标左键** 就行了。断点可以移动，用鼠标拖拽便是。断点可以暂时取消，即是点一下让它变成浅蓝色。断点可以删除，只要把它 **拖曳出行号区** 就行了，就像 Dock 一样直观操作。

现在我把断点设在 `some_function(number)` 这一行。

![vfg8tE4zQ7WLTmd5LaC9_Screen Shot 2013-12-01 at 17.01.39.png][16]

然后执行程序，先在 Console 里输入数字，再按下 Enter 输入到程序里。接着，程序会立刻暂停，你会看到程序码里面，标示了停在哪一行，而 Debug Area 左侧还会出现目前存在的区域变量。Debug Area 有个工具列，上面有几个重要的按钮，用途如图：

![XWNHYGL2QOoCWmgLaVvU_Screen Shot 2013-12-01 at 17.03.13.png][17]

这里要先介绍通常 Debugger 会有的指令：

* **Continue （继续）** ：离开 Debugger 继续执行程序，可能会中断在下一个断点
* **Step Over （跳过）** ：跳过（执行）这一行，然后停在下一行
* **Step Into （跳入）** ：目前在的这一行有函式，跳进去
* **Step Out （跳出）** ：目前在的这一行是在某个函式里面，跳出去到呼叫函式的程序（也就是 **return** 完毕）
熟悉这四个指令，你就可以在程序码之间游走了。

接着我再多设两个断点，分别在 `i_am_a_global_variable +=` 和 `another_function(&some_local_var);` 这两行（不必先把程序停下来，直接按鼠标左键加断点）。然后按下 **Continue** ，当它执行到 `another_function` 这行之前，就会再停下来进入 **Debugger** 。

你会发现左边也有变化，因为进入了 **Function Call** 的 Stack 。你可以在不同的 **Stack** 之间切换，左边也会出现不同的 **Local Variables**，切换的方式是按下 **Debugger** 浏览列的 **function name**。

![KdsfA4OIR2ypOq0icUvz_Screen Shot 2013-12-01 at 17.22.23.png][18]

接着再按一下 **Continue**，会跑进 **another_function** 里面，你会发现在左边窗格会显示传进去的指标的记忆体位址和指标所指的记忆体内容，以及，因为这个 **function** 有参照 (reference) 到全域变量 `i_am_a_global_variable` ，所以 Xcode 也会自动列出：

![77lVASa8Qkuz5L0HFF7H_Screen Shot 2013-12-01 at 17.39.20.png][19]

再来一个小示例，这次是阵列：

```
#include <stdio.h>

int main(void)
{
  int array[] = {1, 2, 3, 4, 5};
  int i;
  for (i = 0; i < 5; i++) {
    printf ("array #%d is %d\n", i, array[i]);
  }
  return 0;
}
```

断点设在 printf 那一行，然后执行，你会发现它把阵列的内容也列出来了（按 ▼ 可以展开）：

![yjLIoJnRZyBaafGPSLsB_Screen Shot 2013-12-01 at 17.42.55.png][20]

那如果是动态产生的阵列呢？

我们知道 malloc, calloc, realloc 传回来的是它所分配到的记忆体的开头位址，那 Xcode 会不会很聪明的把它当作阵列呢？

我们把上面这段程序修改成 `calloc` 的方式：

```
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
  int *array = (int *) calloc(5, sizeof(int));
  int i;
  for (i = 0; i < 5; i++) {
    array[i] = i + 1;
    printf ("array #%d is %d\n", i, array[i]);
  }
  free(array);
  return 0;
}
```

把断点设在 free(array) 那一行，然后执行，你会发现 Debugger 并不会列出 array 的内容，而是只有指标：

![doMqxDEeQhWlg2qsvKPI_Screen Shot 2013-12-01 at 17.48.49.png][21]

从上图我们知道两件事：

* array 声明成 `int *`，所以 Xcode 抓的是它的记忆体位址。
* 它用 int 去解读 `*array` 指向的记忆体内容，所以得到的是首项的值 1，因为 array 的内容是 1, 2, 3, 4, 5。
那如果要看 array[1] 或其他内容的话怎么办呢？这时候就要用 `Expression Monitor `了，可以在这个 `variable` 列表里面按右键选 `Add Expresssion...` ，然后输入 `array[1]` 就行了。另外，既然是 `Expression` ，当然可以输入运算式，例如 `array[1] + 2` 。

![fkWkuuYTIetHNbUsvbc7_Screen Shot 2013-12-01 at 17.57.08.png][22]

Debugger 我会用的功能大概就这样... 不过我觉得这样也就够了，用这些就足以抓出逻辑上的错误。

### 字型设定

我们每天看 code 的人，总是希望它们要长得顺眼，才看得下去。Xcode 当然也可以调整字型。

进入 Xcode 的 Preferences 设置，在 Fonts & Colors 分页里面。不过每个项目是分开的，要一次改的话，是先按 Command + A 全选，然后按下 T 那个 icon ，就可以一次改全部了。附带一提， Console 的字型是在同一个画面的**「Console」**分页里面。

![aZSJS60pQsOMmAJqywGb_Screen Shot 2013-12-01 at 18.18.32.png][23]

再附带一提，我用的字体是 Adobe 出的 **Source Code Pro** ，可以免费下载。

我会的大概也就这些，不知道算不算新手入门了... 


  [1]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/1881336444.png
  [2]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/3206407604.png
  [3]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/2252698502.png
  [4]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/4216545304.png
  [5]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/2848521779.png
  [6]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/4271991838.png
  [7]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/3382825878.png
  [8]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/3672500730.png
  [9]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/3094034774.png
  [10]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/607366666.png
  [11]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/3862308590.png
  [12]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/2086906167.png
  [13]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/1208910803.png
  [14]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/558588382.png
  [15]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/1719871648.png
  [16]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/3673774978.png
  [17]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/1625199242.png
  [18]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/519360877.png
  [19]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/3230502856.png
  [20]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/2686494002.png
  [21]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/2268931632.png
  [22]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/1120655467.png
  [23]: http://7xl0td.com1.z0.glb.clouddn.com/2016/03/01/1437300829.png