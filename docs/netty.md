## Netty
> Netty是一款性能卓越的网络NIO框架，它封装了底层JDK复杂的NIO实现，为开发者提供了良好的API，大大简化了
> 网络应用的开发过程，一般来说，网络框架的开发绕不开以下几个核心点
>
> - I/O模型、线程模型和事件处理机制
> - API接口
> - 数据协议、序列化
>

### I/O模型
> I/O请求可以分为两个阶段，分别为调用阶段和执行阶段
> - 调用阶段：用户进程向内核进程发起系统调用
> - 执行阶段：内核等待I/O请求处理完成返回，此过程又可以分为两个步骤：首先等待数据就绪，并写入内核缓冲区；
> 随后将内核缓冲区的数据拷贝纸用户态缓冲区，如下图所示：

![I/O模型](images/Snipaste_2021-10-07_22-56-17.png)

既然I/O的过程已经了解，那么需要先清除I/O模型有哪些？
* **同步阻塞I/O（BIO）**

* **同步非阻塞I/O（NIO）**

* **I/O多路复用**

* **信号驱动I/O**

* **异步I/O**


