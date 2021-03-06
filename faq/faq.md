# 常见问题

1. UIoT Edge现在支持的官方子设备驱动有哪些？

   目前支持Modbus，支持RTU和TCP方式。未来陆续推出其他协议的驱动。

2. UIoT Edge函数计算如何使用？

   支持Python3，在handler函数里面，处理业务逻辑（如消息过滤、加工），使用function_sdk包里的EdgeClient，实现消息发送，配合消息路由实现编排。请参考[函数计算的例子](/uiot-edge/user_guide/edge_computing/function_development)。

3. 子设备上云，需要的最少配置什么？

   子设备与驱动的绑定配置和一条消息路由配置。

4. 如何实现本地子设备联动？

   可以通过函数计算与消息路由，实现本地场景联动。

5. 如何配置，实现本地缓存断网续传？

   目的地是UIoT云平台的消息路由，打开缓存开关。

6. 如果要开发自己的子设备驱动，如何做？

   官方提供了一个RelaySwitcher驱动例子（模拟继电器开关状态的变化上报），驱动SDK章节有详细说明，可参阅[子设备驱动](/uiot-edge/edge_development/subdev_driver_SDK/python3_SDK_intro)。

   目前SDK支持Python3和C语言。

7. 如何实现网关设备替换？

   目前可以通过重新配置，后面会提供一键替换功能。
   
8. 安装Edge Runtime时出现“unable to resolve host address...”，该怎么处理？

   很可能是系统设置的dns server解析比较慢或出问题了，可以多尝试几次，或者将dns server设置为114.114.114.114（在/etc/resolv.conf里），这个是电信dns server，一般能正常解析。


