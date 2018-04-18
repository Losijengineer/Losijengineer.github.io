[TOC]

# 第0章	前言

​	为什么要叫“第0章”呢？

​	这一章是专门为了接下来的知识做准备，以及处理一些繁琐的事。

​	Brainfuck是一个玄学的语言，它太玄学了以至于网络上很难找到它的编译器和资料，现在在这里放出几个链接：

- https://fatiherikli.github.io/brainfuck-visualizer/
  - Github上的一个Brainfuck程序**可视化**在线编辑器。


- http://files.cnblogs.com/icejoywoo/DBFI.zip
  - 这是一个免费的Brainfuck编译器，还带有许多的例子。
- http://4mhz.de/bfdev.html
  - 这是一个Brainfuck开发端的网站，上面有详细的介绍，往下拉可以看见下载链接。同样是免费的。
  - 这个编译器还提供了"pbrain语言扩展"，具体说明请看网页。
- https://baike.baidu.com/item/Brainfuck/1152785?fr=aladdin
  - 百度百科上的Brainfuck的解释，还有一些例子。
- http://www.muppetlabs.com/~breadbox/bf/
  - 看起来像是Brainfuck的官网，有对Brainfuck详细的解释。
- https://en.wikipedia.org/wiki/Brainfuck
  - Wiki上的Brainfuck介绍。
- http://www.hevanet.com/cristofd/brainfuck/
  - 一个提供很多Brainfuck例子的网站
- http://www.parkscomputing.com/2014/04/pbrain/
  - PBrain拓展的介绍（在第5章会详细地讲）



​	Brainfuck虽说不是一门正规的语言，但多写写Brainfuck的代码可以让你的大脑思维得到发散，提高你的思维能力。~~而不是脑子像be fucked了一样~~。


# 第1章	什么是Brainfuck?

### 第1节	简介

**Brainfuck**是一种**极小化**的计算机语言，它是由**Urban Müller**在1993年创建的。（由于fuck在英语中是一个~~玄学~~的词汇，这种语言有时被称为Brainf**k，甚至被简称为BF）它写出来的程序有的长这样：

```
                            Linus Akesson presents:
                   The Game Of Life implemented in Brainfuck

       +>>++++[<++++>-]<[<++++++>-]+[<[>>>>+<<<<-]>>>>[<<<<+>>>>>>+<<-]<+
   +++[>++++++++<-]>.[-]<+++[>+++<-]>+[>>.+<<-]>>[-]<<<++[<+++++>-]<.<<[>>>>+
 <<<<-]>>>>[<<<<+>>>>>>+<<-]<<[>>>>.+<<<++++++++++[<[>>+<<-]>>[<<+>>>>>++++++++
 +++<<<-]<[>+<-]>[<+>>>>+<<<-]>>>[>>>>>>>>>>>>+>+<<     <<<<<<<<<<<-]>>>>>>>>>>
>>[-[>>>>+<<<<-]>[>>>>+<<<<-]>>>]>      >>[<<<+>>  >-    ]<<<[>>+>+<<<-]>[->[<<<
<+>>>>-]<[<<<  <+>      >>>-]<<<< ]<     ++++++  ++       +[>+++++<-]>>[<<+>>-]<
<[>---<-]>.[- ]         <<<<<<<<< <      <<<<<< <         -]++++++++++.[-]<-]>>>
>[-]<[-]+++++           +++[>++++        ++++<     -     ]>--.[-]<,----------[<+
>-]>>>>>>+<<<<< <     <[>+>>>>>+>[      -]<<<      <<   <<-]>++++++++++>>>>>[[-]
<<,<<<<<<<->>>> >    >>[<<<<+>>>>-]<<<<[>>>>+      >+<<<<<-]>>>>>----------[<<<<
<<<<+<[>>>>+<<<      <-]>>>>[<<<<+>>>>>>+<<-      ]>[>-<-]>++++++++++[>+++++++++
++<-]<<<<<<[>>>      >+<<<<-]>>>>[<<<<+>>>>>      >+<<-]>>>>[<<->>-]<<++++++++++
[>+<-]>[>>>>>>>      >>>>>+>+<<<<      <<<<<      <<<<-]>>> >>     >>>>>>>[-[>>>
>+<<<<-]>[>>>>       +<<<<-]>> >       ]>> >           [<< <        +>>>-]+<<<[>
>>-<<<-]>[->[<      <<<+>>>>-]         <[ <            < <           <+>>>>-]<<<
<]<<<<<<<<<<<, [    -]]>]>[-+++        ++               +    +++     ++[>+++++++
++++>+++++++++ +    +<<-]>[-[>>>      +<<<-      ]>>>[ <    <<+      >>>>>>>+>+<
<<<<-]>>>>[-[> >    >>+<<<<-]>[>      >>>+< <    <<-]> >    >]>      >>[<<<+>>>-
]<<<[>>+>+<<< -     ]>[->[<<<<+>      >>>-] <    [<<< <    +>>       >>-]<<<<]<<
<<<<<<[>>>+<< <     -]>>>[<<<+>>      >>>>> +    >+<< <             <<-]<<[>>+<<
-]>>[<<+>>>>>      >+>+<<<<<-]>>      >>[-[ >    >>>+ <            <<<-]>[>>>>+<
<<<-]>[>>>>+<      <<<-]>>]>>>[ -    ]<[>+< -    ]<[ -           [<<<<+>>>>-]<<<
<]<<<<<<<<]<<      <<<<<<<<++++ +    +++++  [   >+++ +    ++++++[<[>>+<<-]>>[<<+
>>>>>++++++++ +    ++<<<     -] <    [>+<- ]    >[<+ >    >>>+<<<-]>>>[<<<+>>>-]
<<<[>>>+>>>>  >    +<<<<     <<      <<-]> >    >>>>       >>>[>>+<<-]>>[<<+<+>>
>-]<<<------ -    -----[     >>      >+<<< -    ]>>>       [<<<+> > >>>>>+>+<<<<
<-]>>>>[-[>> >    >+<<<<    -] >     [>>>> +    <<<<-       ]>>> ]  >>>[<<<+>>>-
]<<<[>>+>+<< <    -]>>>     >>           > >    [<<<+               >>>-]<<<[>>>
+<<<<<+>>-                  ]>           >     >>>>>[<             <<+>>>-]<<<[>
>>+<<<<<<<                  <<+         >      >>>>>-]<          <<<<<<[->[<<<<+
>>>>-]<[<<<<+>>>>-]<<<<]>[<<<<<<    <+>>>      >>>>-]<<<<     <<<<<+++++++++++[>
>>+<<<-]>>>[<<<+>>>>>>>+>+<<<<<-]>>>>[-[>     >>>+<<<<-]>[>>>>+<<<<-]>>>]>>>[<<<
+>>>-]<<<[>>+>+<<<-]>>>>>>>[<<<+>>>-]<<<[     >>>+<<<<<+>>-]>>>>>>>[<<<+>>>-]<<<
[>>>+<<<<<<<<<+>>>>>>-]<<<<<<<[->[< <  <     <+>>>>-]<[<<<<+>>>>-]<<<<]>[<<<<<<<
+>>>>>>>-]<<<<<<<<<+++++++++++[>>> >        >>>+>+<<<<<<<<-]>>>>>>>[-[>>>>+<<<<-
]>[>>>>+<<<<-]>>>]>>>[<<<+>>>-]<<< [       >>+>+<<<-]>>>>>>>[<<<+>>>-]<<<[>>>+<<
<<<+>>-]>>>>>>>[<<<+>>>-]<<<[>>>+<        <<<<<<<<+>>>>>>-]<<<<<<<[->[<<<<+>>>>-
 ]<[<<<<+>>>>-]<<<<]>[<<<<<<<+>>>>>      >>-]<<<<<<<----[>>>>>>>+<<<<<<<+[>>>>>
 >>-<<<<<<<[-]]<<<<<<<[>>>>>>>>>>>>+>+<<<<<<<<<<<<<-][   lft@df.lth.se   ]>>>>>
   >>>>>>>[-[>>>>+<<<<-]>[>>>>+<<<<-]>[>>>>+<<<<-]>>]>>>[-]<[>+<-]<[-[<<<<+>>
       >>-]<<<<]<<<<<<[-]]<<<<<<<[-]<<<<-]<-]>>>>>>>>>>>[-]<<]<<<<<<<<<<]

        Type for instance "fg" to toggle the cell at row f and column g
                   Hit enter to calculate the next generation
                                 Type q to quit
```

(原帖地址：http://www.linusakesson.net/programming/brainfuck/index.php)

也有的长这样：

```
,.
```

​	Brainfuck的作者立志要创造出一个**简单**而又**玄学**的语言，所以他发明了**Brainfuck**。这个语言正如它的名字一样，程序很难看懂（~~但可以装逼~~），但程序的确是**可以运行**的！

​	这个语言只有**八个字符**作为该语言中的所有语句，而且这个语言是按照**完整图灵机（Turing complete）**思想设计的语言（就是很厉害的一个思想）。除了指令，这个机器还包括：一个以**字节**为单位、被初始化为**零**的**数组**（就是栈）、一个指向该数组的**指针**（初始时指向数组的第一个字节）、以及用于**输入输出**的两个**字节流**（就是管输入输出的一个东西）。

​	**Brainfuck就是一个完整的图灵机模型**。（图灵机就是一个很厉害的机器）

> ​	Müller的目标是建立一种简单的、可以用最小的编译器来实现的、符合图灵完全思想的编程语言。这种语言由八种状态构成，为Amiga机器编写的编译器（第二版）只有240个字节大小！
>
> ​	就像它的名字所暗示的，brainfuck程序很难读懂。尽管如此，brainfuck图灵机一样可以完成任何计算任务。虽然brainfuck的计算方式如此与众不同，但它确实能够正确运行。
>
> ​	这种语言基于一个简单的机器模型，除了指令，这个机器还包括：一个以字节为单位、被初始化为零的数组、一个指向该数组的指针（初始时指向数组的第一个字节）、以及用于输入输出的两个字节流。
>
> ​	这种语言，是一种按照“Turing complete（完整图灵机）”思想设计的语言，它的主要设计思路是：用最小的概念实现一种“简单”的语言，BrainF**k 语言只有八种符号，所有的操作都由这八种符号的组合来完成。

​	（以上文字均摘自百度百科，不代表个人观点）

### 第2节	为什么要学Brainfuck?

​	看到了上面的代码，你可能会问：**“为什么我要学Brainfuck这种无聊的语言呢？”**

​	的确，Brainfuck不是一个正规的语言，几乎没有一个**OJ（Online Judge，在线评测系统）**支持Brainfuck（~~但SPOJ支持~~）。但它毕竟是一个**最小的图灵完备语言**，还是一个**能够正常运行的**、**极为迷(xuan)你(xue)的**语言。它极大限度地挑战了你的思维与智商。能否正确且最优地写出一个问题的Brainfuck解，完全靠你那过人的才能了。

### 第3节	练习

​	从现在开始，每一章的最后一节是专门用来放练习题的，你可以在讲义的最后看到这些习题的答案与解析（解析不一定会有），不过你最好先思考一下这些习题......

- Brainfuck是一种什么样语言？

- Brainfuck是基于什么思想的？

- 在Brainfuck中，一共有几种语句（或说有几种状态）？

- OJ是什么？

- 以下代码中，哪一个是Brainfuck的代码？

  - ```c++
    #include <iostream>
    using namespace std;
    int main(){
    	cout<<"Hello,world!"<<endl;
        return 0;
    }
    ```

  - ```
    +++++++++++++++.>
    -----.>
    [,>>++.<<.]-+++.
    ```

  - ```java
    public class HelloWorld {
        public static void main(String[] args) {
        System.out.println("Hello World!");
        }
    }
    ```

  - ```python
    print("Hello,world!")
    ```



# 第2章	栈		

### 第1节	回顾

​	**栈（stack）**这个东西我相信大家肯定学过，就是一个先入后出的**线性表**。栈就是仅允许在表的一端进行插入和删除运算。这一端被称为**栈顶**，相对地，把另一端称为**栈底**。向一个栈插入新元素称作**进栈（push）**，也称**入栈**或**压栈**，它是把新元素放到栈顶元素的上面，使之成为新的栈顶元素；从一个栈删除元素又称作**出栈（pop）**或**退栈**，它是把栈顶元素删除掉，使其相邻的元素成为新的栈顶元素。

![栈](https://s1.ax1x.com/2018/03/31/9xrSWd.jpg)



​	因为大家都挺了解的，所以现在给出C++代码实现，让大家再更深入地了解一下：

```c++
//这段代码用到了一个stack头文件，它自带了栈这个东西。
#include<iostream>
#include<stack>//为了便捷地使用栈
using namespace std;
int main(){
    stack <int>stk;//定义一个栈
    //栈的定义方法为： stack <栈元素的类型> 栈的名字;
    //将1~50这50个数入栈
    for(int i=1;i<=50;i++){
        stk.push(i);//将元素i入栈
    }
    cout<<"栈的大小:"<<stk.size()<<endl;//引用栈的大小
    //直到栈空为止，一直出栈
    while(!stk.empty()){
        //栈是否为空的判断方法： 栈的名字.empty()
        //栈不为空时返回1，否则返回0
        cout<<stk.top()<<endl;//获取栈顶元素
        stk.pop();//弹出栈顶元素
    }
    cout<<"栈的大小:"<<stk.size()<<endl;
    return 0;
}
```

### 第2节	栈与Brainfuck

​	为什么我要讲栈这个东西呢？因为它和Brainfuck或多或少有着一点联系。现在，我们要从Brainfuck内部工作原理说起：

​	Brainfuck内部是一个无限长（你可以看成是无限长的）的数组，你可以理解为一列火车。其中，程序开始时有一个指针指向第一个空间，你可以理解为有一个乘务员在第一间车厢里。通过一系列的代码，你可以在这一个数组里操作，好比加减ASCLL值，移动指针指向的空间等，你可以理解为这个乘务员在车厢与车厢间穿梭，乘务员也会在某个车厢里添加或减少乘客数。

​	你可以发现，这个Brainfuck的工作原理和栈或多或少有一点联系。栈是通过指针来获得某一个空间的值，Brainfuck也类似。不过栈和Brainfuck，的确，没多大联系，你大可以把之前讲的栈知识当做复习。

### 第3节	练习

- 栈是什么？
- 栈需要遵守哪四个字的规定？
- 简述栈的实现方法。
- 简述Brainfuck的工作原理。
- 完成下表：

| 类型\语言 | Brainfuck |  栈  |
| :-------: | :-------: | :--: |
|  相同点   |           |      |
|  不同点   |           |      |



# 第3章	程序入门

### 第1节	基本操作

​	现在开始**真正地**学习Brainfuck了！

​	Brainfuck内置了八个字符，分别对应八种语句，其关系如下：

| 字符 |                             含义                             |
| :--: | :----------------------------------------------------------: |
|  >   |                  指针加一（移向下一个单元）                  |
|  <   |                  指针减一（移向上一个单元）                  |
|  +   |                    指针指向的字节的值加一                    |
|  -   |                    指针指向的字节的值减一                    |
|  .   |              输出指针指向的单元内容（ASCLL码）               |
|  ,   |             输入内容到指针指向的单元（ASCLL码）              |
|  [   | 如果指针指向的单元值为零，向后跳转到对应的 ] 指令的次一指令处 |
|  ]   | 如果指针指向的单元值不为零，向前跳转到对应的 [ 指令的次一指令处 |

​	注意：Brainfuck中所有字符都是以**ASCLL码（American Standard Code for Information Interchange，美国信息交换标准代码）**为准的，所以你不要想在Brainfuck里输出**汉字**、**俄语字母**等ASCLL码里**不存在的东西**！（虽然ASCLL码的乱码里面有一些奇怪的汉字）

​	有些人就会问了，**这个"["和"]"的含义我看不懂啊**。没关系，给你一张Brainfuck转C语言的表格（假设p是char*类型）：

| Brainfuck |      C       |
| :-------: | :----------: |
|     >     |     ++p;     |
|     <     |     --p;     |
|     +     |    ++*p;     |
|     -     |    --*p;     |
|     .     | putchar(*p); |
|     ,     | *p =getch(); |
|     [     | while (*p) { |
|     ]     |      }       |

​	简单来说，"["与"]"之间构成的区域就是一个**循环体**，只有当里面的值为**0**的时候循环才会终止（注意：这里的“值为0”的意思是：指针指向的空间**操作完毕**后的值为0），否则一直循环下去。**循环可以嵌套。**

​	还有一点，在Brainfuck程序里，除了上述提到的八个字符以外的所有字符都将被当做注释处理，这使得在Brainfuck里写注释非常方便。

​	好了，知道了这些，你就已经可以开始写得一手漂亮的Brainfuck代码了！就好比：

```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
++++++++++++++++++++++++++++++++++++++++++++.>
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.>
+++++++++++++++++++++++++++++++++.>
```

​	**可别被吓着！**这只是输出 Hello,world! 的**最笨的**一个方法，原理就是通过增加每一个空间里的ASCLL码使其达到 Hello,world! 的样子。我说了，这是**最笨的**一个方法，聪明点的长这样：

```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.
+++++++++++++++++++++++++++++.
+++++++..
+++.
-------------------------------------------------------------------.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.
--------.
+++.
------.
--------.
-------------------------------------------------------------------.
```

​	通过加减一个空间里的ASCLL值来达到 Hello,world! 的样子。当然，还有更聪明的，我们以后再讲。

​	还记得我之前说过，在Brainfuck程序里，除了那八个字符以外的所有字符都将被当做注释处理，所以你大可以这么写：

```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.输出H
+++++++++++++++++++++++++++++.输出e
+++++++..输出ll
+++.输出o
-------------------------------------------------------------------.输出,
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.输出w
--------.输出o
+++.输出r
------.输出l
--------.输出d
-------------------------------------------------------------------.输出!
```

​	很方便，不是吗？

~~~
,.
~~~

​	这段代码的作用就是从**键盘**读取**一个字符**并输出到**屏幕**上。对啊，很简单啊！但要注意几点：

- 这段代码**只能输入一个字符**，多的会被抛弃掉。
- 别想着输入**中文**，如果你真的想要那样做的话......

```
Input：
我要输入中文
Output：
?聼螾佑矋岕矊˶Â
```

​	可以看到，输出了一堆奇怪的东西（而且每次输出的东西还不一样）。

​	那如果我想输入五个字符呢？你可能会写出：

```
,,,,,.....
```

​	但如果你运行一下的话，就会发现：

```
Input:
12345
Output:
55555
```

​	为什么会出现这样的情况？还记得一开始讲过的栈吗？

​	程序开始时，指针指向第一个元素。现在连续输入五次，而每次输入的值都将覆盖上一个值，所以导致成了输入12345，结果就是5。然后在指针位置没变的情况下连续输出五次，毫无疑问地输出五个5。那我想输入12345输出12345怎么办呢？没错：

```
,>,>,>,>,<<<<.>.>.>.>.
```

​	这段代码将每次输入的一个字符存在一个空间里，然后输出时返回第一个位置，一个一个地往后输出。还有一种办法：

```
,.,.,.,.,.
```

​	这个就不用移位，因为输入一个字符后立刻输出，输入下一个字符后之前的字符就没用了（已经输出了），不用担心占位的问题。

​	假如我想输入一个不定长的字符串并输出，要如何做呢？代码短得惊人：

```
,[.,]
```

​	这条代码用到了两个新的东西："["和"]"。这其实是一个循环体的标识符，具体规则上面已经讲过了。程序先输入了一个字符，之后进入循环，每次循环输出之前输入的字符。

​	再来一个问题：实现10以内的加法（输入形如a+b）。（提示：一个数字字符的ASCLL码值减去48等于这个数本身，再利用循环将这两个值加在一起并加上48后输出）

```
,>++++++           输入第一个数并设置后一个空间内的值为6，为下面的循环次数做准备
[<-------->-]      循环6次，每次对第一个数减去8，共减去6*8=48
,,                 输入加号和第二个数，第二个数覆盖了加号（加号本来就没用）
[<+>-]             将第二个数加到第一个数里（第2节会着重讲）
,<.                输入回车并输出第一个空间内的值（即两数相加之和）
>.                 输出你刚刚输入的回车
```

​	程序做的无非就是下面两条：

- 将原来为字符的第一个数通过减去48而转换为了数字
- **将第二个数（未减去48）加到第一个数里，得到两数之和加上48，恰好为一个字符**

### 第2节	典型语句串

现在开始介绍一些拼凑起来的常用语句串，至于为什么，我相信你能理解的：

```
[-]
```

​	作用：清零当前指针指向的空间里的值。

```
[[-]<]
```

​	作用：清零当前指针和前面的所有指针指向的空间里的值。

```
>,[.>,]
```

​	作用：输出输入的字符串。与之前不同的是，这些字符串是可以**重复利用**的，而不是一次性的。

```
[->+<]
```

​	作用：将当前指针指向的空间的值加到后一个空间里。

```
+++++++++++++++++++++++++++++++++.> 初始化输出字符，在此例中为"!"
++++ 调整这里的加号数量n，使得输出n+1个"!"
[<.>-] 主循环部分
```

​	作用：输出n+1个某字符。

```

```





### 第3节	例题剖析

**Hello World!**

```
++++++++++                                 初始化第一个空间的值为10，为后面循环次数做准备
[>+++++++>++++++++++>+++>+<<<<-]           循环，为输出做准备
>++.>+.+++++++..+++.                       输出“Hello”
>++.                                       输出“ ”
<<+++++++++++++++.>.+++.------.--------.   输出“World”
>+.>.                                      输出“!”以及换行
```

**分析**：

​	代码第一行将第一个空间的值调为10（ASCLL码对应换行符），第二行进入循环体：

​	1.移到下一个空间并将其值+7

​	2.移到下一个空间并将其值+10

​	3.移到下一个空间并将其值+3

​	4.移到下一个空间并将其值+1

​	5.返回第一步并将其值-1（这里减的是第一个空间的值。因为第一个空间的值为10，所以该循环体会循环10次）

​	可以看出，在循环体结束之后，每一个空间里的值如下表：

|    1    |    2    |     3     |    4    |    5    | ...  |
| :-----: | :-----: | :-------: | :-----: | :-----: | :--: |
| 10-10=0 | 7*10=70 | 10*10=100 | 3*10=30 | 1*10=10 |  0   |

​	当第10次循环至第5步时，操作完毕后第一个空间的值为0，所以退出循环，来到程序的第三行至第六行：（此时指针指向第一个空间）

​	1.移到第二个空间并调整其值为70+2=72（H），输出

​	2.移到第三个空间并调整其值为100+1=101（e），输出

​	3.指针不移动，将第三个空间的值增加为101+7=108（l），输出两遍

​	4.指针仍不移动，	将第三个空间的值增加为108+3=111（o），输出

​	（此时得到“Hello”）

​	5.移到第四个空间并调整其值为30+2=32（空格），输出

​	6.回到第二个空间并增加其值为72+15=87（W），输出

​	7.移到第三个空间直接输出原来的值（o）

​	8.指针不移动，调整第三个空间的值为111+3=114（r），输出

​	9.指针仍不移动，调整第三个空间的值为114-6=108（l），输出

​	10.指针仍不移动，调整第三个空间的值为108-8=100（d），输出

​	（此时得到“ World”）

​	11.移到第四个空间，调整其值为32+1=33（!），输出

​	12.移到第五个空间，调整其值为10+1=11（换行），输出

​	（此时得到“Hello World!”）
