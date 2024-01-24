
并发的关键是有处理多任务能力，但不一定同时；并行的关键是你有同时处理多个任务能力。

**多线程、协程属于并发操作，多进程属于并行操作。**

\begin{itemize}
    \item 多线程：由于全局锁（GIL）存在，并发是多个线程轮流使用CPU，同一时刻仅一个线程工作，操作系统在核实时间切换。
    由于线程切换速度快，感觉是多个任务“同时运行”。在I/O密集型任务场景中，线程切换后，I/O操作仍然进行，如线程1进行I/O操作时，线程2可同时获得CPU资源进行计算。虽增加了切换成本，但提高了效率。
    \item 协程：是轻量级线程，是单线程，却可执行并发任务，是由于协程把切换权利交给程序员。协程可处理上万并发，多线程则不可以（切换成本太大，将耗尽计算机资源）。
    \item 多进程：并行，真正同一时刻多个任务同时进行。想使用多核，就用多进程。
\end{itemize}

Python协程标准库只有一个，即asyncio；而支持多线程、多进程的标准库则有两个：Concurrent.futures和Multiprocessing。
 
\begin{lstlisting}
from multiprocessing.dummy import Pool as ThreadPool
with ThreadPool(processes=100) as executor:
    executor.map(func, iterable)
\end{lstlisting}
