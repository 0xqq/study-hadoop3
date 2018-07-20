## 踩坑记录：

### hostname配置错误

> `./start-dfs.sh`后，jps发现master启动了DataNode、ResourcesManager、Nodemanager、NameNode，查看日志也没有报错，而且其他机器telnet master的9000和50070端口不通。

   排查后发现：

   - slave1和slave2没有做免密登陆master

   - 3台机器的/etc/hosts文件设置错误

     ```shell
     127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4 centos-1
     ::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
     
     192.168.56.101 centos-1
     192.168.56.102 centos-2
     192.168.56.103 centos-3
     ```

     **按照这个配置，从下往上找hostname对应的ip，所以Hadoop所有的服务都起在127.0.0.1上，所以其他机器都反问不了，所以改为以下，瞬间解决问题**

     ```shell
     127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
     ::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
     
     192.168.56.101 centos-1
     192.168.56.102 centos-2
     192.168.56.103 centos-3
     ```


