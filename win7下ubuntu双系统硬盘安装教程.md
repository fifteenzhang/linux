# linux
the start of  ubuntu 14.10
win7下ubuntu双系统安装教程

1.ubuntu14.10下载
  地址：http://old-releases.ubuntu.com/releases/utopic/
  我用的ubuntu-14.10-desktop-amd64.iso
  此处注意amd64位为64位操作系统，i386为32位

2.EasyBCD下载：链接为2.3个人版http://jiangxi.jz5u.com:8087/soft-2015/EasyBCD%20dwj.rar
  2.1 打开EasyBCD软件
  2.2 选择添加新条目
  2.3 NeoGrub 配置
  2.4 在跳出的menu.list中用以下覆盖
          title Install Ubuntu
          root (hd0,0)
          kernel (hd0,0)/vmlinuz.efi boot=casper iso-scan/filename=/ubuntu-14.10-desktop-amd64.iso ro quiet splash locale=zh_CN.UTF-8
          initrd (hd0,0)/initrd.lz
          
          注意:
          ubuntu-14.10-desktop-amd64.iso是你下载的ubuntu iso的名字，改成你自己的。
          有的电脑如有问题，出现filesystem type is ntfs partition type 0x07
          有如下几种错误（按顺序排除）：
                          1.ubuntu-14.10-desktop-amd64.iso是否与下载的iso一致
                          2.vmlinuz.efi initrd.lz名称是否一致 包括后缀！
                          3.安装时根据电脑C盘符的位置选择错误 (hd0,0)改为（hd0,x）【假设C盘为第二个则（hd0,1)】。
                              不清楚的可以右键计算机 管理 磁盘管理 查看C盘在第几个。

3.下载好的Ubuntu 14.10 iso镜像文件用压缩软件或者虚拟光驱打开，casper文件夹下的initrd.lz和vmlinuz文件，.disk文件夹解压到C盘根目录，把iso文件也复制到C盘根目录。再次注意这几个文件名称以及后缀是否与上一步bcd menu.list中的一致

4.重启电脑
  在引导界面出现win7和NeoGrub 引导加载器两个选项，选择NeoGrub 引导加载器
  等待

5.点击Install Ubuntu  等待一段时间后进入桌面，会有两个图标，一个是安装，暂时勿动

6.要按Ctrl+Alt+T 打开命令终端，输入代码sudo umount -l /isodevice这一命令，否则可能出现找不到分区
    注意，这里的-l是L的小写
    -l 与 /isodevice 有一个空格
    
7.点击安装Ubuntu 14.10  选择语言 若选择安装时更新要联网（随意）
      此处可能出现:
                  选择完语言等闪退到桌面的情况，则再次点击安装即可
                  点击安装没反应（一般点击安装鼠标会变成进度环）或者假死
                      判断是否假死及解决方案
                              鼠标不能动————强制重启
                              crtl+atl+t能打开————等待一段时间，不行重新点击安装
                              crtl+atl+t不能打开—————ctrl+alt+F1，算了还是重启吧

8.安装类型 其他选项（可以自己调整分区大小，推荐）

9.双击未分配区域/点击change处的+
  推荐分配方案  20G以上 主分区   用于 ext4 挂载点/ （我用了50G）
                 3G     逻辑分区 用于 交换空间（SWAP）

10.按提示继续至安装完毕，重启

                              
                              

                          
          
  
