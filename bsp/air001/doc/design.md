# Air001虚拟设备

虚拟设备本身是一个进程, 实现LuatOS的API, 并暴露控制接口, 通过可视化界面或命令行客户端进行操作

## 基本架构

```
Linux/Docker -- 虚拟设备 -- 控制API -- 界面/命令行客户端
```


## 基本要求

1. 可配置, 按指定配置文件进行启动, 例如指定内存大小,可用库等
2. 可控制, 通过控制API, 主动推送设备变化, 被动接受控制指令
3. 安全性, 不对宿主机有破坏性的操作
4. 隔离性, 同一个宿主机应该支持多个虚拟设备同时运行

## 与其他Luat虚拟环境的对比

1. [luatvm](https://github.com/xs-soft/luatvm) 基于Golang实现的Luat虚拟机, 以lua代码兼容性为切入点
2. TODO

这些虚拟环境, 均以luatask库的兼容性为切入点, 其实也是LuatOS最早的版本所考虑的方式, 实现一套与当前LuaTask的Lua C API完全兼容的底层实现.

本文所讲述的,是另外一套实现, 从C API的层面去进行虚拟.

对比Air742U的C SDK, 其实有实现一套虚拟C SDK的意思. 只不过,这里实现的是LuatOS的include目录里面的一套C API.

## 已知的困难

1. 宿主不是实时操作系统, 该虚拟设备在一定程度上需要模拟成实时操作系统(涉及msgbugs和timer的实现)
2. 模拟外设的实现难度, 例如如何模拟uart呢
3. 模拟真实传感器的实现难度, 例如如何模拟DS18B20的响应呢?
4. disp库的模拟也是一个不小的挑战

## 详细设计

TODO 待定

https://www.freertos.org/FreeRTOS-simulator-for-Linux.html
