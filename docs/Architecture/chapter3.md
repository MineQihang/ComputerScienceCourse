nWhat is Instruction Set Architecture? How is it represented? * 指令集架构

nRISC vs. CISC *

nClassifying Instruction Set Architectures by the type of internal storage in a processor * 内部存储类型

nInstruction Characteristics

nEndian order * 端序/字节序   小端和大端   以及  对齐(alignment)

nStructure of Recent Compilers: Multi-pass structure

nMIPS Architecture & MIPS Instruction Format

什么是ISA?How is it represented(如何表示指令)?:
a set of instructions,且每条指令都是由cpu硬件来执行的.  用二进制的形式存储指令集,有定长指令和不定长指令.

RISC与CISC
CISC：复杂指令集架构，追求更强大的指令，减少程序的指令条数，并交由硬件实现。

RISC：精简指令集架构，追求更少更简单的指令和更低的CPI

RISC设计原则：

简单统一的指令格式（所有指令长度均相同），减少寻址方式
每条指令的功能应尽可能简单，并在一个机器周期内完成
只有load store可以访存，其他操作都是在寄存器上
以简单有效的方式支持高级语言
强调优化编译器的作用
强调流水线技术
ISA的分类（分类依据：用来存放操作数的存储单元类型）:


                                          (其中寄存器型又包括r-r型和r-m型)



只有寄存器型沿用至今,区分GPR ISA的方法是看指令中mem address的个数和操作数(operands)的个数



ALU指令中，存储器操作数个数和操作数个数的所有可能组合只有七种,不可能有(3,2),也就是指令有三个地址却只需要两个操作数.



 

小端序和大端序:
小端序：低字节保存在低地址

大端序：低字节保存在高地址

举例：

var = 0x11223344，对于这个变量的最高字节为0x11，最低字节为0x44

(1)大端模式存储（存储地址为16位）         (2)小端模式存储（存储地址为16位）

地址                      数据                                             地址                    数据

0x0004(高地址)  0x44                                   0x0004(高地址)        0x11

0x0003                 0x33                                        0x0003                 0x22

0x0002                 0x22                                        0x0002                 0x33        

0x0001(低地址)   0x11                                   0x0001(低地址)       0x44


————————————————
版权声明：本文为CSDN博主「ASR_THU」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/zongza/article/details/83780572