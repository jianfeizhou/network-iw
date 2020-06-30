 wget    http://www.infradead.org/~tgr/libnl/files/libnl-3.2.25.tar.gz
 wget    https://mirrors.edge.kernel.org/pub/software/network/iw/iw-4.0.tar.gz
 tar -xvf libnl-3.2.25.tar.gz 
 tar -xvf iw-4.0.tar.gz 

 mdir tallball
 mkdir  -p   tallball
 mv *.gz tallball/

 cd libnl-3.2.25/
 ./configure --host=arm-linux --prefix=/home/jianfeizhou/work/7.iw/install
 make clean
 make
 make install

 cd ..
 cd iw-4.0/
 export PKG_CONFIG_PATH=/home/jianfeizhou/work/7.iw/install/lib/pkgconfig:$PKG_CONFIG_PATH
 make CC=arm-linux-gcc

 

测试：
 拷贝install 和 iw 
export LD_LIBRARY_PATH=/mnt/usbmounts/sdb/install/lib:/mnt/usbmounts/sda/install/lib:$LD_LIBRARY_PATH
iw
iw list // 列出WIFI网卡的性能
ifconfig wlan0 up //启用wifi模块
iw dev wlan0 scan // 扫描可连接WIFI AP
iw wlan0 connect dswei // 连接到不加密的WIFI，WIFI名字为dswei
iw wlan0 connect dswei keys d:0:baiwenwang123 // 连接到WEP加密的WIFI，WIFI名为dswei，d: default, 0: 第0个密码