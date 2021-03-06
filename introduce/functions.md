# 功能介绍

UIoT Edge产品是UCloud IoT为工业、能源、楼宇等需要本地实时响应、就近计算、多协议接入的场景而提供的一套软件运行时，客户可以直接部署到符合要求的x86、arm硬件平台上，实现设备接入、边缘计算等功能。

UIoT Edge提供子设备接入、函数计算、消息路由、消息远程SSH运维，提供完整的边缘端解决方案。

### 边缘网关管理

功能包括：

- 边缘网关的添加、删除、修改、查询；
- 边缘网关的启用、禁用、状态查询、部署、部署状态查询等；
- 边缘网关的子设备列表、驱动分配、函数分配、消息路由配置、监控信息查看；
- 边缘网关子设备的绑定、解绑、启用、禁用；
- 边缘网关的通用设备功能，包括[Topic管理](https://docs.ucloud.cn/uiot-core/console_guide/product_device/topic)、[物模型](https://docs.ucloud.cn/uiot-core/console_guide/thingmode/what_is_thingmode)、[设备影子](https://docs.ucloud.cn/uiot-core/console_guide/device_shadow/waht_is_deviceshadow)、[设备调试](https://docs.ucloud.cn/uiot-core/console_guide/monitoring_maintenance/online_debug)；

### 子设备管理

提供对子设备的全生命周期管理，查看子设备的相关信息，所属网关等。

功能包括：

- 子设备的添加、删除、修改、查询；
- 子设备所属网关信息；
- 子设备的通用设备功能，包括[Topic管理](https://docs.ucloud.cn/uiot-core/console_guide/product_device/topic)、[物模型](https://docs.ucloud.cn/uiot-core/console_guide/thingmode/what_is_thingmode)、[设备影子](https://docs.ucloud.cn/uiot-core/console_guide/device_shadow/waht_is_deviceshadow)、[设备调试](https://docs.ucloud.cn/uiot-core/console_guide/monitoring_maintenance/online_debug)；

### 驱动管理

子设备驱动，用户可以根据子设备接入的特有协议，适配驱动框架，从而方便子设备的快速接入。

功能包括：

- 驱动的添加、删除、修改、下载；
- 驱动的基本信息展示，包括通信协议、开发语言、CPU架构、驱动类型等；
- 驱动分配到网关；
- 驱动配置，包括网关设备层的配置、子设备层的配置；

### 函数计算

函数计算是一种数据处理规范，方便用户定义自己的数据处理与业务逻辑，比如就近控制、数据解析、数据清洗、数据脱敏等。

功能包括：

- 函数的添加、删除、修改；
- 函数的基本信息展示，包括函数名称、函数描述、开发语言等；
- 函数计算分配到网关；

### 消息路由

消息路由可以配置不同源到不同目的地的消息流转路径。每条消息路由包含三要素：消息源、源消息的主题过滤、消息目的地。消息源和目的地可以是UIoT Core（云端）、函数计算、子设备。

### 远程SSH运维

基于WebSSH方式，方便用户远程登录网关设备，进行运维工作；默认关闭。
