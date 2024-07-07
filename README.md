# Linux-Monitor
# 分布式Linux性能监控系统

## 项目简介

目前该系统支持CPU状态，系统负载，软中断，mem，net监控，易于扩展更多系统监控。

本项目整体结构图如下：

![image-20240707221813935](C:\Users\钟邦乾\AppData\Roaming\Typora\typora-user-images\image-20240707221813935.png)

## 系统功能

1.monitor模块：采用工厂方法，通过构造moniotr的抽象类定义接口，后实现相应的CPU状态，系统负载，软中断，mem，net监控，易于为之后扩展更多系统监控；并为了模拟出真实的性能问题，使用stress工具进行模拟压测，分析相应时刻服务器的cpu状况和中断状况。

2.通过grpc框架，构建出相应的server， client；server在所要监控的服务器部署，client生成库供monitor模块和display模块调用，并考虑为了降低耦合性，项目每个模块相互独立，可拆解，只通过调用grpc服务来进行远程连接。

3.使用protobuf序列化协议，构建出整个项目的数据结构。
