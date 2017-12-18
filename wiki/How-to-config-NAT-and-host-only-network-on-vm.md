# 用NAT网络实现共享上网（通过主机的上网卡），用host-only网卡为主机和各个虚机组成内网，但不能上网（故该网不设gateway)
1. 在主机上正确安装virtual box
2. 网络全局设置如下图
  ![](../image/%E5%85%A8%E5%B1%801.png)
  ![](../image/%E5%85%A8%E5%B1%802.png)
3. 此时主机会虚拟出一块hostonly网卡,而NAT所用网卡则为与实际网卡共享，因此可通过该网卡访问internet
  ![](../image/%E4%B8%BB%E6%9C%BAhostonly%E8%99%9A%E6%8B%9F%E7%BD%91%E5%8D%A1.png)
4. 虚机网卡配置如下图
  ![](../image/%E8%99%9A%E6%9C%BA%E7%BD%91%E5%8D%A1%E9%85%8D%E7%BD%AEnat.png)
  ![](../image/%E8%99%9A%E6%9C%BA%E7%BD%91%E5%8D%A1%E9%85%8D%E7%BD%AEhostonly.png)
5. 虚机启动后，会有两个虚拟网卡enp0s3和enp0s8，（可用命令ifconfig看）
  enp0s3的默认配置是自动获得地址，为NAT网段的地址，同时会有default gateway 如下图
   ![](../image/%E8%99%9A%E6%9C%BA%E7%BD%91%E5%8D%A1%E9%85%8D%E7%BD%AEnat%E5%AE%9E%E9%99%85%E5%B1%9E%E6%80%A71.png)
  通过ubuntu的网络配置工具可对enp0s8进行配置，可以分配固定ip地址
  不同虚机给不同的ip，比如我的主机ip是192.168.122.1，master虚机为192.168.122.20，node1虚机为192.168.122.30.但不要设default gateway，因为上网走的是NAT网络
6. 最终的路由类似下图（用route命令看）
  ![](../image/%E8%99%9A%E6%9C%BA%E7%BD%91%E5%8D%A1%E9%85%8D%E7%BD%AEnat%E5%AE%9E%E9%99%85%E5%B1%9E%E6%80%A7%E9%BB%98%E8%AE%A4%E8%B7%AF%E7%94%B1.png)
7. 此时你的虚机即可以上网，又可以与主机连成局域网进行通讯了。


