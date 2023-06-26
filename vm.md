


# 移动硬盘
[参考](https://www.likecs.com/show-264003.html)

菜单VM -> Removable devices -> Kingston DataTraveler 2.0 (自己硬盘的名字) -> Connect (Disconnect from host)


# 其他
修改配置文件中所对应的虚拟磁盘
修改：win10_dong.vmx
scsi0:0.fileName = "/data1/vm/win10_notebook_all_2021-3-26 21_33_22.vmdk"


提高CPU资源分配
修改程序的优先级为-20
sudo top后按“r”–>输入进程PID–>输入nice值


打开虚拟机，出现“无法打开内核设备:\\Global\\vmx86”这样的提示:
将下面的代码复制到一个.txt文件里面，文件名自己定，什么鬼都没所谓

@Echo Off 
:: 解决虚拟机无法打开内核设备"\\.\Global\vmx86
title Hankcs's program
color 8F
CD 
%~d0
CD %~dp0
vnetlib -- uninstall vmx86
vnetlib -- install vmx86
pause

注意，第二行可以不要，因为“::”相当于c语言里面的//注译一行代码
然后保存，重命名文件为.bat文件
最后你只需要将这个.bat文件拷贝到你vmware安装文件夹中双击运行，那么当你重新打开虚拟机的时候，发现整个世界都亮了
