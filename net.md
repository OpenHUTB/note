


# shadowsock
[参考](https://shadowsockshelp.github.io/Shadowsocks/linux.html)
```shell script
wget https://github.com/shadowsocks/shadowsocks-qt5/releases/download/v3.0.1/Shadowsocks-Qt5-3.0.1-x86_64.AppImage
```

1.在全局模式下，所有的网站都默认走代理（使你的所有http/socks数据经过代理服务器的转发送出。）
2.在PAC(Proxy Auto Config)模式是只有被墙了的网站才会走代理（连接网站的时候读取PAC文件里的规则，来确定你访问的网站有没有被墙，如果符合，那就会使用代理服务器连接网站）。



inet_ntop: numeric(uint32)->presentation(点分十进制)

点分十进制IPv4的地址，最长16个char
201.199.244.101"就是一个最大可能长度的例子，再加上一个NULL结束符

IPv6最多46个字符
1.X:X:X:X:X:X:X:X，如 "CDCD:910A:2222:5498:8475:1111:3900:2020" 这是纯IPv6地址
2.X:X:X:X:X:X:d.d.d.d，如 "0001:0002:0003:0004:0005:ffff:111.112.113.114" 这是与IPv4混合的IPv6地址（最长）
3.加前缀的IPv6， X:X:X:X:X:X:d.d.d.d/前缀 , 如 "12AB:0000:0000:CD30:0000:0000:0000:0000/60"
