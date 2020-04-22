# 物联网边缘网关

UIoT Edge产品是UCloud IoT为工业、能源、楼宇等需要本地实时响应、就近计算、多协议接入的场景而提供的一套软件运行时，客户可以直接部署到符合要求的x86、arm硬件平台上，实现设备接入、边缘计算等功能.

UIoT Edge提供子设备接入框架、函数计算、消息路由、远程SSH运维、AI推理等功能，提供完整的边缘端解决方案。

TODO：

1. 网关本地控制台使用
2. 边缘端开发：驱动SDK、函数计算SDK
3. 云端API接口
4. 最佳实践
5. 版本更新说明
6. 其他：
   - 驱动的测试
   - Modbus驱动示例、驱动配置、子设备配置
   - 脚本安装软件，对系统的一些要求：硬件、系统、工具软件版本
   - 函数开发，event、context的解释
   - 函数计算的测试
   - 消息路由的测试
   - 远程运维


命名规范：

1.产品名称：UIoT Core、UIoT Edge、UIoT SDK等

遗留问题：

1. 消息路由的唯一标识是name，而不是相同的源、topic、目的地；所以配置两条规则一样的，将会触发两次；



目前完成章节：

- [产品简介](iot/uiot-edge/产品简介)

  - [什么是物联网边缘网关](iot/uiot-edge/产品简介/什么是物联网边缘网关.md)
  - [功能介绍](iot/uiot-edge/产品简介/功能介绍.md)
  - [名词解释](iot/uiot-edge/产品简介/名词解释.md)
  - [使用要求及限制](iot/uiot-edge/产品简介/使用要求及限制.md)
  - [产品计费模式](iot/uiot-edge/产品简介/产品计费模式.md)

- [使用指南](iot/uiot-edge/产品计费模式)

  - [使用流程概述](iot/uiot-edge/使用指南/使用流程概述.md)
- [创建网关及子设备](iot/uiot-edge/使用指南/创建网关及子设备)
  
  - [创建网关](iot/uiot-edge/使用指南/创建网关及子设备/创建网关.md)
    - [创建子设备](iot/uiot-edge/使用指南/创建网关及子设备/创建子设备.md)
    - [关联子设备](iot/uiot-edge/使用指南/创建网关及子设备/关联子设备.md)
    - [网关管理](iot/uiot-edge/使用指南/创建网关及子设备/网关管理.md)
  - [安装网关软件](iot/uiot-edge/使用指南/安装网关软件) 
- [安装软件](iot/uiot-edge/使用指南/安装网关软件/安装软件.md)
  
  - [子设备驱动与接入](iot/uiot-edge/使用指南/子设备接入)
- [概览](iot/uiot-edge/使用指南/子设备接入/概览.md)
    - [驱动开发及添加](iot/uiot-edge/使用指南/子设备接入/驱动开发及添加.md)
  - [分配驱动](iot/uiot-edge/使用指南/子设备接入/分配驱动.md)
    - [子设备接入协议](iot/uiot-edge/使用指南/子设备接入/子设备接入协议.md)
- [添加边缘计算](iot/uiot-edge/使用指南/添加边缘计算)
  - [概览](iot/uiot-edge/使用指南/添加边缘计算/概览.md)
    - [函数开发及添加](iot/uiot-edge/使用指南/添加边缘计算/函数开发及添加.md)
    - 分配函数
  - [运行函数计算](iot/uiot-edge/使用指南/添加边缘计算/运行函数计算.md)

- [设置消息路由](iot/uiot-edge/使用指南/设置消息路由)
  
    - [概览](iot/uiot-edge/使用指南/设置消息路由/概览.md)
    - [添加消息路由](iot/uiot-edge/使用指南/设置消息路由/添加消息路由.md)
  - [消息路由配置详解](iot/uiot-edge/使用指南/设置消息路由/消息路由配置详解.md)
  
- [远程运维管理](iot/uiot-edge/使用指南/远程运维管理)
  
  - [远程访问](iot/uiot-edge/使用指南/远程运维管理/远程访问.md)
  
