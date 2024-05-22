戴尔 Optiplex 7060 台式电脑

处理器：因特尔Core i5-8500T

内存  ：16 GB（金士顿DDR4 2666MHz 8GB ／镁光DDR4 2400MHz 4GB x 2）

显卡  ：英特尔UHD Graphics 630(128 MB /戴尔）

主板  ：戴尔ONC2VH (Q370 芯片组）

硬盘  ：西数 WD BLACK SN770.500GB (500 GB / 固态硬盘）

网卡  ：英特尔Ethernet Connection 1219-LM/戴尔

声卡  ：英特尔 High Definition Audio （ALC255）


BIOS 设置

1:System Configuration--SATA Operation--AHCI

2:Secure Boot--Secure Boot Enable--Disabled

4:Intel® Software Guard Extensions™--Intel® SGX™--Disabled

修改DVMT 使用这个工具（modGRUBShell）核显能不能驱动这一步很关键

需要用modGRUBShell执行以下命令（引导里面已经配有modGRUBShell）

• setup_var Ox8DC 0x0x2(修改DVMT为64MB）

• setup_var Ox5BE Ox00（关闭CFG Lock)


引导完善程度：

声卡

网卡

核显

DP接口

3.5耳机接口

睡眠唤醒

以上已经完美驱动

后续有问题我会更进
