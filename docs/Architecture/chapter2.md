## Power：功耗

### 动态功耗

- traditionally dominant component：传统上占主导地位的部分？
- dissipated when transitor switches ：晶体管切换

#### Dynamic energy

Transistor switch from 0 -> 1 or 1 -> 0
$$
\text {Energy}_\text{dynamic} \propto \frac12 \times \text{Capacitive load} \times \text{Voltage}^2
$$

#### Dynamic power

$$
\text {Power}_\text{dynamic} \propto \frac12 \times \text{Capacitive load} \times \text{Voltage}^2 \times \text{Frequency switched}
$$

**ATTENTION**: Reducing clock rate reduces power, **NOT** energy.

#### Techniques for reducing power

- Do nothing well
- Dynamic Voltage-Frequency Scaling (**DVFS**)
- Low power state for DRAM, disks
- Overclocking, turning off cores

> 例子：DVFS is a low-power design technique that is becoming  pervasive in modern processors
>
> If the **voltage** and **frequency** of a processing core are both  **reduced by 15%** what would be the impact on dynamic power?
>
> ![image-20221107111139398](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107111139398.png)

### 静态功耗

- becoming more important with transitor scaling：随着晶体管规模的扩大而变得更加重要
- due to  "leakege current" that flows  even if there is no switching activity：由于 "泄漏电流 "的存在，即使没有开关活动，也会流动
- proportional to the number of transitors on the chip：与芯片上的晶体管数量成正比

$$
\text {Power}_\text{static} \propto \text{Current}_\text{static} \times \text{Voltage}
$$

- Scales with number of transistors

- To reduce: power gating



## Cost：价格/成本

- Cost driven down by learning curve: 成本因学习曲线而降低
  - Yield: 产量
- DRAM: price closely tracks cost: 价格紧跟成本
- Microprocessors: price depends on volume: 微处理器：价格取决于体积
  - 10% less for each doubling of volume

### Integrated Circuit Cost：集成电路成本

- Integrated circuit

$$
\text{Cost of intergrated circuit} = \frac{\text{Cost of die} + \text{Cost of testing die} + \text{Cost of packaging and final test}}{\text{Final test yield}}
$$

$$
\text{Cost of die} = \frac{\text{Cost of wafer}}{\text{Dies per wafer} \times \text{Dies yield}}
$$

$$
\text{Dies per wafer} = \frac{\pi \times (\frac{\text{Wafer diameter}}{2})^2}{\text{Die area}} = \frac{\pi \times \text{Wafer diameter}}{\sqrt{2\times \text{Die area}}}
$$

- **Bose-Einstein formula**

  下面的$\text{Defect per unit area}$一般为$0.016-0.057$ defects per square  cm(2010)；

  $N$为process-complexity factor = $11.5-15.5$ (40 nm, 2010)

$$
\text{Die yield} = \text{Wafer yield}\times \frac{1}{(1+\text{Defect per unit area}\times \text{Die area})^N}
$$

> ![image-20221107104646708](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107104646708.png)

> ![image-20221107104705481](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107104705481.png)



## Performance：性能

评价指标：

- Time to run the task：execution time（执行时间）, response time（反应时间）, elapsed time（经历时间）, **latency**（时延）
- Tasks per time unit：execution rate（执行率）, bandwidth（带宽）, throughput（吞吐量）

### Latency vs. Throughput

#### Latency

- “real” time necessary to complete a task
- important when the focus is on a **single task**
  - a computer user who is working with a single application
  - a critical task of a real-time embedded system

#### Throughput (aka Bandwidth)

- **number of tasks completed per unit of time**
- a metric independent from the exact number of executed tasks
- important when the focus is on running **many tasks**
  - a manager of a large data-processing center is interested in the total amount of work done in a given time

#### Example: Pipelining

- **increases** the instruction **throughput**
- does **NOT reduce** (in fact, it usually slightly increases)  **the execution time of an individual instruction**



### Performance Metrics

- Machine X is $n$ times faster than machine Y
  $$
  n = \frac{executionTime(Y)}{executionTime(X)}=\frac{performance(X)}{performance(Y)}
  $$



### Benchmark Suites：测试套件？

Sets of **programs** to **simulate** typical workloads

- real software applications
  - most accurate but typically longer to process
  - portability problems (OS/compiler dependencies), GUI
- kernels
  - small, key pieces taken from real programs
  - limited picture, but good to isolate the performance of individual features of a machine
- synthetic benchmarks
  - try to match the average frequency of operations on operands of a real program
  - try to match the average frequency of operations on operands of a real program



### Principle of Locality：局部性原理

#### Temporal Locality：空间局部性

a resource that is **referenced** at one point in time **will be referenced again** sometime in the near future

一个资源引用完后，旁边的资源很可能马上被用到

#### Spatial Locality：时间局部性

the likelihood of referencing a resource is higher if a resource **near it was just referenced**

一个资源引用完后，同一个资源很可能马上被用到

#### Example: Cache

- directly exploits **temporal locality** providing faster access to a smaller subset of the main memory which contains copy of data recently used
- all data in the cache are not **necessarily data**  that are spatially close in the main memory
- when a cache miss occurs a fixed-size block of contiguous memory cells is retrieved from the main memory based on the principle of **spatial locality**



### “Make the Common Case Fast”

- in making a design trade-off…
  - favor the frequent case rather than infrequent case
- when determining how to allocate resources…
  - favor the frequent event rather than the rare event
- when optimizing the design of a module…
  - target the average functional behavior



### Amdahl’s Law

What is frequent case and how much performance improved by making case faster

- Speedup_enhanced(增强加速比)：改进部分采用改进措施后比没有采用改进措施前性能提高倍数(旧时间/新时间)
  $$
  speedup = \frac{originalExecutionTime}{originalExecutionTime}=\frac{newPerformance
  }{originalPerformance}
  $$
- Fraction_enhanced(增强比例)：计算机执行某个任务的总时间中可被改进部分的时间所占的百分比.

If component $x$ is improved by $S_x$ and component $x$ affects a fraction $F_x$ of the overall execution time then
$$
speedup = \frac{1}{(1-F_x)+F_x / S_x}
$$

![img](https://img-blog.csdnimg.cn/20181106112753775.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pvbmd6YQ==,size_16,color_FFFFFF,t_70)

> Example1:
>
> If we optimize the module for  the floating-point instructions  by a factor of 2, but the  system will normally run  programs with only 20% of  floating point instructions  then the speedup is only
> $$
> speedup = \frac{1}{(1-0.2)+0.2/2}=\frac{1}{0.9}=1.111
> $$

> Example2:
>
> ![image-20221107162152025](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107162152025.png)

Amdahl定律告诉我们：系统中某一部件由于采用某种更快的执行方式后,整个系统性能的提高与这种执行方式的使用频率或占总执行时间的比例有关。



### CPU Time

- user CPU Time
  - spent in the user program
- system CPU Time
  - spent in the OS performing tasks required by the program
  - harder to measure and to compare across architectures
- CPU performance = user CPU time on an unloaded  system
- CPU Time = (Clock Cycles for a Program) x (Clock Cycle  Time)  = (Clock Cycles for a Program) / (Clock Frequency)

-  IC = Instruction Count
  - number of instructions executed for a program

- **CPI = Clock cycles Per Instruction**
  - average number of clock cycles per instruction of a program
- IPC = Instruction Per Clock cycles
- **CPU Time = IC x CPI x CCT** (CCT: Clock Cycle  Time)

![image-20221107153617481](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107153617481.png)

![img](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/2018110611310277.png)
$$
\text{CPU Time} = \sum_i (\text{IC}_i \times \text{CPI}_i) \times \text{CCT}
$$

$$
\text{CPI} = \sum_i (\frac{\text{IC}_i}{\text{IC}}\times \text{CPI}_i)=\sum_i(\text{IF}\times \text{CPI}_i)
$$

> Example
>
> ![image-20221107154628404](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107154628404.png)
>
> ![image-20221107154701043](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107154701043.png)
>
> ![image-20221107154717270](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107154717270.png)



### Improving Performance by Exploiting Parallelism：并行

- at the system level
  - use multiple processors, multiple disks
    - scalability is key to adaptively distribute workload in server apps
- at the single microprocessor level
  - exploit instruction level parallelism (ILP)
    - e.g., pipelining overlaps the execution of instruction to reduce  the overall program CPU Time
      - reduces CPI by overlapping instructions in time
      - possible because many subsequent instructions are independent
    - e.g. parallel computation
      - reduces CPI by overlapping instructions in space
      - duplicate hardware modules such as ALUs
- at the circuit level
  - carry-lookahead adders speed-up sums
    - from linear to logarithmic



## Instruction Set Principles：ISA

the computer visible to the assembler  language programmer or compiler writer



































