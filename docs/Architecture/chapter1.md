## 背景

### big.LITTLE

大核：高性能计算；小核：低能耗

![image-20221107100336305](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107100336305.png)

### 四堵墙

- **频率墙**：工艺进入超深亚微米后，线延时超过门延时而占据主导地位；

- **功耗墙**(Power Wall)：漏流增大，功耗增大，导致芯片过热，器件的稳定性下降，信号噪声增大，无法正常工作；

- **存储墙**(Memory Wall)：通信带宽和延迟构成；

- **应用墙**：每一种处理器在各自的领域内都有着很高的性能。但如果应用条件发生变化则会导致性能明显下降，导致通用微处理器并不通用。

### 基础定义

![image-20221107100816182](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107100816182.png)



## C&A：计算机系统结构

![image-20221107102007225](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107102007225.png)

- classical definition：程序员所看到的计算机的属性，即程序员编写出的能在机器上正确运行的程序所必须了解到的概念性结构和功能特性。

- broadest definition：使用各种可行的制造工艺进行抽象层的设计，使得应用程序有效运行。



## 摩尔定律

- **集成电路芯片上所集成的电路的数目，每隔18个月就翻一番。**
- **微处理器的性能每隔18个月提高一倍，而价格下降一倍。**

![image-20221107102907534](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107102907534.png)

### 新摩尔定律

- DLP比TLP带来的并行计算的能力增长更多
- 翻倍的不再是晶体管(集成电路)和处理器速度,而是**processor的数量**,未来计算机硬件不会更快,但是会**更宽**.(比如并行处理能力)



## 冯·诺依曼计算机

![image-20221107103834114](https://qihang-1306873228.cos.ap-chongqing.myqcloud.com/imgs/image-20221107103834114.png)



