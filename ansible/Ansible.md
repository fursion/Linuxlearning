# Ansible

## 安装

Ansible 基于Python开发，需要保证设备上具有Python环境
```conf
sudo apt install -y ansible
```
## 配置文件介绍
### 配置文件 ansible.cfg
文件路径 /etc/ansible/ansible.cfg
1. 分类和优先级
    ![image-20221202143754906](..\src\image-20221202143754906.png)
2. 常用配置参数
    ![image-20221202143932283](..\src\image-20221202143932283.png)

### hosts[主机列表]
文件路径/etc/ansible/hosts

将需要控制的主机iP地址或者Host地址登记在此文件中

```
192.168.1.1
#192.168.1.1 ansible_ssh_port=22 ansible_ssh_user=root ansible_ssh_pass='passwd' 单个设置用户名和密码。
[web]
192.168.1.2
192.168.1.3
[webapi]
192.168.1.4
192.168.1.5
[webservice:children] #子组
web
webapi
#根据组进行端口，用户名，密码设置
[web:vars]
ansible_ssh_port=22
ansible_ssh_user=root
ansible_ssh_pass='passwd'
[all:vars] #all代表全部主机
ansible_ssh_port=22
ansible_ssh_user=root
ansible_ssh_pass='passwd'
```



## 基本命令

![image-20221202144056836](..\src\image-20221202144056836.png)

## Ansible Module

- Ansible AD-Hoc ansible命令行批量执行命令(使用各种模块)

### 命令/脚本相关模块

| Ansible模块 |                                            |      |
| :---------- | ------------------------------------------ | :--- |
| ping模块    | 检查ansible与主机连通性                    |      |
| shell模块   | 批量执行shell命令或脚本                    |      |
| command     | 批量执行简单命令(不支持特殊符号，默认模块) |      |
| script      | 脚本分发模块                               |      |
|             |                                            |      |

- shell
```bash
#使用格式
#   指定主机清单    主机组  指定模块    指定动作(参数)
ansible -i hosts <group> -m shell -a 'hostname'
```
- command是ansible默认的模块(不指定模块时，默认就使用ansible模块)

```bash
  
  ```

  

- script

```bash
  ansible -i hosts <group> -m script -a 'exp.sh'
  ```


### 文件相关模块
