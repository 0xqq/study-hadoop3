## 准备虚拟机环境

| 主机名   | IP地址         | 角色                                      |
| -------- | -------------- | ----------------------------------------- |
| centos-1 | 192.168.56.101 | master<br />NameNode<br />ResourceManager |
| centos-2 | 192.168.56.102 | slave1<br />SecondNameNode                |
| centos-3 | 192.168.56.103 | slave2                                    |

### 修改hostname

`hostnamectl set-hostname centos-1`

`hostnamectl set-hostname centos-2`

`hostnamectl set-hostname centos-3`

### 修改/etc/hosts

在

