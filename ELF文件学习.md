### ELF文件概述

#### ELF文件定义

​		ELF(Executable and Linkable Format)文件是一种目标文件格式，常见的包括：可执行文件、可重定位文件(.o)、共享目标文件(.so)、核心转储文件等。

#### ELF文件的结构

​		一个完整的ELF文件一般会包括如下几个内容：ELF头、Section头、Program头和Section。

​		其中由Section头组成的集合称为Section头表，由Program头组成的集合称为Program头表。注意：数个连续的头称之为头表，**头表是虚拟出来的定义，文件中不存在头表，只有头**。

​		一个Section头指向一个Section，Section头中包括所指向Section的**名字、类型、其在ELF文件中的偏移地址、大小等信息**。

​		**一个Program头指向一个Segment**，Program头中包括所指向Segment的类型、其在ELF文件中的偏移地址、大小，映射到内存的虚拟地址等信息。**一个Segment由一系列连续的Section构成**，连续的Section拥有相同的权限，如只读、读写、可读可执行等。

​		一个ELF头内包含有：Section头表的在ELF文件中的偏移地址、单个Section头的大小、Section头表中Section头的个数；Program头表的在ELF文件中的偏移地址、单个Program头的大小、Program头表中Program头的个数；该ELF文件的类型，若是可执行文件的话，还包含的有程序的入口地址。