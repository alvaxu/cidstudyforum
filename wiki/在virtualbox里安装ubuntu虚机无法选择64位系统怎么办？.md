1	在virtualbox里安装ubuntu虚机无法选择64位系统怎么办？
详细问题：在新建的时候只能选择32位系统： 
 ![](../master/1.png)
解决思路:
1. 32位|64位的系统都可以安装64位的虚拟机。VirtualBox安装64位的系统需要满足两个条件：1. 64位的cpu，这个不会有人有问题。2. cpu允许硬件虚拟化。这个需要在BIOS里确认：
  开机进入BIOS，setup==>security==>cpu virtualization，如果cpu virtualization这一项的值是Disable，然后设置为Enable。保存，然后重启电脑，硬件虚拟化就开启成功了。
  2.但win10的机子可能还会有问题，就是hyper-V服务会独占件虚拟化，我们需要在服务里面把hyper-V相关的服务都禁掉：


