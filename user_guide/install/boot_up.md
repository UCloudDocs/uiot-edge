# 开机自启动设置



 使用`systemd`管理` IoT Edge`

您可以使用`systemd`来管理` IoT Edge`服务的启动（start）、停止（stop）和查看状态（status）。

` IoT Edge`的`systemd service`如下所示。新建一个文件`IoTEdge.service`

```shell
[Unit]
Description=IoT Edge
After=networking.service

[Service]
Type=forking
Restart=on-failure
ExecStart=/${edge_path}/ucloud_iot_edge_process.sh --start
ExecReload=/${edge_path}/ucloud_iot_edge_process.sh --start
ExecStop=/${edge_path}/ucloud_iot_edge_process.sh --stop
ExecStatus=/${edge_path}/ucloud_iot_edge_process.sh --status

[Install]
WantedBy=multi-user.target
```

拷贝至指定目录。

```shell
sudo cp IoTEdge.service /etc/systemd/system/IoTEdge.service
```

设置开机自启动

```shell
sudo systemctl enable IoTEdge.service
成功时您会看见类似以下输出
Created symlink /etc/systemd/system/multi-user.target.wants/IoTEdge.service → /etc/systemd/system/IoTEdge.service.
```

service文件更改后重新加载。

```shell
sudo systemctl daemon-reload
```

其它常用命令如下所示。

- 启动命令：`sudo systemctl start IoTEdge.service`
- 重启命令：`sudo systemctl restart IoTEdge.service`
- 停止命令：`sudo systemctl stop IoTEdge.service`
- 查看状态：`sudo systemctl status IoTEdge.service`
- 停止全部命令：`./ucloud_iot_edge_process.sh --stop all`
- 禁用开机自启动：`sudo systemctl disable IoTEdge.service`
- 查看服务状态：`systemctl list-unit-files | grep IoTEdge.service`