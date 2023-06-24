## 部署云


### 安装 openstack snap

首先安装 openstack snap：

```
sudo snap install openstack --channel 2023.1
```

### 准备机器

Sunbeam 可以生成一个脚本，以确保计算机安装了所有必需的依赖项，并正确配置了在 MicroStack 中使用 - 您可以使用以下命令查看此脚本：

```
sunbeam prepare-node-script
```

或者可以这样直接执行脚本：

```
sunbeam prepare-node-script | bash -x && newgrp snap_daemon
```

该脚本将确保主机上满足某些软件要求。特别是，它将：

* `openssh-server`如果没有找到则安装
* 为当前用户的所有命令配置无密码 sudo ( `NOPASSWD:ALL`)

### 引导云

使用以下命令部署 OpenStack 云 `cluster bootstrap`并接受软件默认设置：

```
sunbeam cluster bootstrap --accept-defaults
```

### 配置云并获取凭据

现在使用以下命令配置已部署的云 `configure`：

```
sunbeam configure --accept-defaults --openrc demo-openrc
```

上述命令提供普通用户凭据（文件 `demo-openrc`）。可以通过以下方式获取管理员凭据（文件 `admin-openrc`）：

```
sunbeam openrc > admin-openrc
```

## 启动虚拟机

通过启动基于“ubuntu”映像（Ubuntu 22.04 LTS）的名为“test”的虚拟机来验证云。`launch`使用命令：

```
sunbeam launch ubuntu --name test
```

示例输出：

```
Launching an OpenStack instance ...
Access instance with `ssh -i /home/ubuntu/.config/openstack/sunbeam ubuntu@10.20.20.200`
```

使用提供的命令通过 SSH 连接到 VM。
