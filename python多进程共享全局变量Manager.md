由于多进程之间内存相互独立，默认情况下无法直接共享全局变量。
为了解决此问题，python提供了Manager()类，能创建一个共享的命名空间，
使多个进程可以访问和修改其中的变量。

**进程&线程**
---
对操作系统来说，一个任务就是一个进程(Process)，比如打开一个浏览器或word。有些进程同时做多件事情，也就是同时运行多个“子任务”，进程内的子任务是线程(Thread)。
程序编写后没有运行时程序，正在运行代码是进程。

multiprocessing模块为在子进程中运行任务、通讯和共享数据，以及执行各种形式同步提供支持。
join(timeout)方法是主进程等待调用join()方法的子进程终止。


Manager()创建共享变量
---
可以使用以下方法来创建Manager创建共享变量，有：
- list(): 创建共享列表
- dict(): 创建共享字典
- Value(): 创建共享值
- Array(): 创建共享数组

