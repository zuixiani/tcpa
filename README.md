# TCPA备份
## 一键脚本
``` bash
wget http://shaojin520.gitee.io/script/TCPA/tcpa.sh
chmod +x tcpa.sh
sh tcpa.sh
```
或者
``` bash
yum install -y wget && wget -O tcpa.sh https://github.com/zuixiani/tcpa/raw/main/tcpa.sh && sh tcpa.sh
```
或者
``` bash
wget https://github.com/zuixiani/tcpa/raw/main/tcpa.sh -O tcpa.sh;sh tcpa.sh
```
## 脚本说明
- 使用命令：lsmod|grep tcpa 出现tcpa_engine 224249 0则表示TCPA安装成功。
- TCPA目录：/usr/local/storage/tcpav2
- 运行TCPA:
``` bash
cd /usr/local/storage/tcpav2
sh start.sh
```
- 增加端口：TCPA默认只加速80、443、8080端口，如果需要增加端口请执行：
``` bash
vi /usr/local/storage/tcpav2/start.sh
#输入i进行编辑
#找到$BINDIR/$CTLAPP access add tip $ip tport 80
#在下方照着复制，改下端口号就行
#键位esc，输入：wq后回车
cd /usr/local/storage/tcpav2
sh start.sh
```

- 卸载TCPA:
``` bash
cd /usr/local/storage/tcpav2
sh uninstall.sh
```

## 手动安装方法
- 1.安装依赖
``` bash
yum -y install net-tools
```
- 2.更换系统内核
``` bash
wget https://github.com/zuixiani/tcpa/raw/main/sh/kernel-3.10.0-693.5.2.tcpa06.tl2.x86_64.rpm
rpm -ivh kernel-3.10.0-693.5.2.tcpa06.tl2.x86_64.rpm --force
```

- 3.重启
``` bash
reboot
```

- 4.下载主程序
``` bash
wget https://github.com/zuixiani/tcpa/raw/main/sh/tcpa_packets_180619_1151.tar.gz
tar xf tcpa_packets_180619_1151.tar.gz
cd tcpa_packets
sh install.sh
cd /usr/local/storage/tcpav2
sh start.sh
```
- 5.查看是否安装成功
``` bash
lsmod|grep tcpa
```