# 计算机操作系统

> 操作系统（Operating System，OS），系统软件，管理与控制计算机硬件与软件资源的计算机程序。

**OS五大管理：**

- **CPU**
- 存储器
- I/O设备
- 文件
- 接口

## 操作系统引论

### 操作系统基本特性

#### 并发（Concurrence）

> 并发：两个或多个时间在**同一时间间隔**内发生
>
> 并行：两个或多个时间**同一时刻**发生

#### 共享（Sharing）

- 互斥共享方式
- 同时访问方式

#### 虚拟（Virtual）

**时分复用技术**

> 利用设备的空闲时间，转去为其他用户服务，使设备得到充分的利用

**空分复用技术**

#### 异步（Asynchronism）

> 异步性又叫不确定性

### 操作系统的主要功能

#### 处理机管理功能（CPU）

- 进程控制
- 进程同步
- 进程通信
- 调度

#### 存储器管理功能

- 内存分配（静态和动态两种方式）
- 内存保护
- 地址映射
- 内存扩充

#### 设备管理功能

- 缓冲管理
- 设备分配
- 设备处理
- 设备无关性

#### 文件管理功能

- 文件存储空间的管理
- 目录管理
- 文件的读/写管理和保护
- 文件操作的一般管理

#### 操作系统与用户之间的接口

- 用户接口
  - 联机用户接口
  - 脱机用户接口
  - 图像用户接口
- 程序接口

### OS结构设计

#### 无结构操作系统

> 难以维护

#### 模块化结构OS

> 模块-接口法，又被称为“无序模块法“

**衡量模块的独立性两个标准**

- 内聚性
- 耦合度

**优点**

- 提高OS设计的正确性、可理解性和维护性
- 增强OS的可适应性
- 加速OS的开发过程

#### 分层式结构OS

> 将模块-接口法中”决定顺序“的无序性变为有序性

**优点**

- 易保证系统的正确性
- 易扩充和易维护性

**缺点**

- 系统效率降低

#### 微内核结构OS

**基本概念**

- 足够小的内核
- 基于客户/服务器模式
- 应用“机制与策略分离”原理
- 采用面向对象技术

**基本功能**

- 进程（线程）管理
- 低级存储器管理
- 中断和陷入处理

**优点**

- 提高系统的可扩展性
- 增强了系统的可靠性
- 可移植性强
- 提供了对分布式系统的支持
- 融入了面向对象技术