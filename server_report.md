


cd /home/ubuntu/git/DFS/server/DFSClient/bin

./client -a 1 -p /home/ubuntu/git/DFS/data/terrain.jpg
/home/ubuntu/git/DFS/server/DFSClient/bin/client -a 2 -i group1/M03/10/6F/ChMTF1i_bGWABgR5AAca_DryEVM8310051***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d ./saved.jpg
/home/ubuntu/git/DFS/server/DFSClient/bin/client -a 3 -i group1/M01/0F/AF/ChMTF1iB4GqASv5CAAca_C2FWzQ3214762***haidong.wang***59748A23C0109D11387CAF69C8255B4A
./client -a 4 -i group1/M03/00/00/ChMTGFlN_m6AfVFiAAca_EYe81k3324803***haidong.wang***59748A23C0109D11387CAF69C8255B4A -e 600000
./client -a 5 -s /home/ubuntu/git/DFS/data/compressed -f /home/ubuntu/git/DFS/data/fileList.txt -t jpg


测试：
./client -a 1 -p ./terrain.jpg
test1/M01/00/00/ChMTF1lSQCSAEHWwAAca_JuuunI5460081***haidong.wang***59748A23C0109D11387CAF69C8255B4A

./client -a 2 -i test1/M02/00/00/ChMTF1lSPZaAYX5RAAca_JuuunI2156118***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d ./saved.jpg

./client -a 4 -i test1/M02/00/00/ChMTF1lSPZaAYX5RAAca_JuuunI2156118***haidong.wang***59748A23C0109D11387CAF69C8255B4A -e 600000

http://10.19.19.23:8080/action.php?fileID=ChsNCk9RM05MUU5OUU5OUT0WMyo4TxItLiQfPycmSyw/Px0fITQLCwsQN0xPS0hPT0ZYGgsbKhcTG0NPSkdHSEhGRkdL


压力测试：
http://10.19.19.24:8080/action.php?fileID=GQwRCw5PUTNOTVFOTlFOTlE9FjMqOTgSMCETSD8YKDgXPz8dHyE7JxtGTxVNTUxKRk5N&dueTime=T0pHR05KT05NRw==

ab -n 10 -c 10 http://10.19.19.24:8080/action.php?fileID=GQwRCw5PUTNOTVFOTlFOTlE9FjMqOTgSMCETSD8YKDgXPz8dHyE7JxtGTxVNTUxKRk5N&dueTime=T0pHR05KT05NRw==
 //访问100次，每次并发10个URL


./client -a 4 -i group1/M03/89/24/ChMTFllRAzmAEbj7AAca_Afq2Ag7196356***haidong.wang***59748A23C0109D11387CAF69C8255B4A -e 600000
http://10.19.19.22:8080/action.php?fileID=GQwRCw5PUTNOTVFGR1FMSlE9FjMqOBISL0YuFz8cSCoNPz8dHyE/OgoXES9JR09LTklN&dueTime=T0pHR05JSEZJTA==




group1/M03/89/24/ChMTFllRAzmAEbj7AAca_Afq2Ag7196356***haidong.wang***59748A23C0109D11387CAF69C8255B4A
http://10.19.19.22:8080/action.php?fileID=GQwRCw5PUTNOTVFGR1FMSlE9FjMqOBISLD8EEz87HBRJPz8dHyE/GA9MPxlJT0dITUtI&dueTime=T0pHR05GT0hMSQ==


测试机器上：
./client -a 1 -p ./terrain.jpg
test1/M00/00/00/ChMTF1lOMXGAQJZxAAca_JuuunI6395913***haidong.wang***59748A23C0109D11387CAF69C8255B4A

./client -a 2 -i test1/M01/00/00/ChMTF1lQb_CAaQTdAAca_JuuunI3704487***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d ./test.jpg

./client -a 4 -i test1/M01/00/00/ChMTF1lQb_CAaQTdAAca_JuuunI3704487***haidong.wang***59748A23C0109D11387CAF69C8255B4A -e 600000

test1/M01/00/00/ChMTF1lQb_CAaQTdAAca_JuuunI3704487

http://10.19.19.23:8080/action.php?fileID=ChsNCk9RM05PUU5OUU5OUT0WMyo4TxIvHCE9Px8vKho/Px0fITQLCwsQN01JTkpKRkk=&dueTime=T0pHR05KTUdPTA==

storage_server_port=23000

异常：
./client -a 4 -i group1/M03/00/00/ChMTGFlN_m6AfVFiAAca_EYe81k3324803***haidong.wang***59748A23C0109D11387CAF69C8255B4A -e 60000
返回：
http://0.78.131.10:8080/action.php?fileID=GQwRCw5PUTNOTVFOTlFOTlE9FjMqOTgSMCETSD8YKDgXPz8dHyE7JxtGTxVNTUxKRk5N&dueTime=T0pHRk1LSElJTg==
 



批量下载
http://www.cnblogs.com/xudong-bupt/p/3504442.html


./client -a 1 -p /home/ubuntu/git/DFS/data/terrain.jpg -f /home/ubuntu/git/DFS/data/fileID_fullPath.txt
./client -a 2 -i group1/M03/10/6F/ChMTF1i_bGWABgR5AAca_DryEVM8310051***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d /home/ubuntu/git/DFS/data/download/saved.jpg
./client -a 3 -i group1/M01/0F/AF/ChMTF1iB4GqASv5CAAca_C2FWzQ3214762***haidong.wang***59748A23C0109D11387CAF69C8255B4A
./client -a 4 -i group1/M03/10/6D/ChMTF1i1PS2AbPdVAAca_B5FSp07544490***haidong.wang***59748A23C0109D11387CAF69C8255B4A -e 30


/home/ubuntu/git/DFS/server/DFSClient/bin/client -a 1 -p /home/ubuntu/git/DFS/data/terrain.jpg          ./client -a 1 -p ./medium.jpg -f ./fileID_fullPath.txt
/home/ubuntu/git/DFS/server/DFSClient/bin/client -a 2 -i group1/M03/10/6F/ChMTF1i_bGWABgR5AAca_DryEVM8310051***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d ./saved.jpg
/home/ubuntu/git/DFS/server/DFSClient/bin/client -a 3 -i group1/M01/0F/AF/ChMTF1iB4GqASv5CAAca_C2FWzQ3214762***haidong.wang***59748A23C0109D11387CAF69C8255B4A
/home/ubuntu/git/DFS/server/DFSClient/bin/client -a 4 -i group1/M03/10/6D/ChMTF1i1PS2AbPdVAAca_B5FSp07544490***haidong.wang***59748A23C0109D11387CAF69C8255B4A -e 30





[2017-03-08 10:22:53] ERROR - file: tracker_proto.c, line: 48, server: 10.19.19.22:23000, response status 2 != 0
group1/M03/10/6F/ChMTF1i_YlqAUnN4AAca_HOjM283131632***haidong.wang***59748A23C0109D11387CAF69C8255B4A

拿fileID来进行请求(这个时候记录有效时间)，返回有时效的url；  --> 用fileID再上传一次，返回临时的URL（时效存下来）
用过来的fileID下载这个文件，再上传，得到fileID（或者直接获得指定fileID的软链接），再（获得对应fileID的文件属性：source ip address）拼接成URL返回给用户；
这个时候开一个线程维护时间，到时删除 <20ms
2下载文件到磁盘
4下载上传返回拼接好的URL


生成的临时URL
http://127.0.0.1:8080/action.php?fileID=BxIPFRBRTy1QU09RUE9WJE8jCC00JlEJUTAzUiECMAQ2ISEDAT8iVSYzEFBXVVRUVFlQ&dueTime=UVRYWFdWVlhZVA==
PPH解密后的URL
http://10.19.19.23:8080/group1/M03/1/D/ChMTF1i1PS2AbPdVAAca_B5FSp7544490


能下载URL： http://10.19.19.22:8080/group1/M03/10/6D/ChMTF1i1PS2AbPdVAAca_B5FSp07544490


上传返回临时URL的方式，
链接最大时长：生成上传文件的软链接（第二个不同于第一个的fileID），超过指定时间则删除软链接

再次上传一次文件，返回第二次上传的fileID，维护这个时间，当超过这个时间的时候就删除它。
为每一个上传有时效文件的请求，新建一个线程来计时，sleep指定时间就delete


减少输入参数：
./client -a 1 -p /home/ubuntu/git/DFS/data/terrain.jpg -f /home/ubuntu/git/DFS/data/fileID_fullPath.txt
./client -a 2 -i group1/M03/10/6F/ChMTF1i_bGWABgR5AAca_DryEVM8310051***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d /home/ubuntu/git/DFS/data/download/saved.jpg
./client -a 3 -i group1/M01/0F/AF/ChMTF1iB4GqASv5CAAca_C2FWzQ3214762***haidong.wang***59748A23C0109D11387CAF69C8255B4A
./client -a 4 -i group1/M03/10/6D/ChMTF1i1PS2AbPdVAAca_B5FSp07544490***haidong.wang***59748A23C0109D11387CAF69C8255B4A -e 30


./client -a 1 -p ./medium.jpg           ./client -a 1 -p ./medium.jpg -f ./fileID_fullPath.txt
./client -a 2 -i group1/M03/10/6F/ChMTF1i_bGWABgR5AAca_DryEVM8310051***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d ./saved.jpg
./client -a 3 -i group1/M01/0F/AF/ChMTF1iB4GqASv5CAAca_C2FWzQ3214762***haidong.wang***59748A23C0109D11387CAF69C8255B4A

HTTP访问：
http://10.19.19.22:8080/group1/M01/0F/AF/ChMTF1iB4LqAaeLTAAca_B2NA841757549






接口说明：
char* client(char* host_ip, int action, char* argList[], int* strLen)
 host_ip: 服务器的IP地址
 action:    执行所需要的动作, 1表示上传，2表示下载，3表示删除
 argList:
    1上传：argList[0]为用户名，argList[1]为fileBuffer, argList[2]fileBuffer(文件)长度, argList[3]为图片压缩质量
    2下载: argList[0]为用户名，argList[1]为下载文件的FileID，argList[2]为下载图片所需的图片质量
    3删除：argList[0]为用户名，argList[1]为所要删除文件的fileID
 strLen:    操作过程修改的变量
    上传后：strLen为返回fileID的长度（失败???）
    下载后：strLen为返回文件的长度
    删除后：strLen为是否删除成功(0表示删除成功，1表示删除失败)

返回char*
    上传(action==1)：返回的char* 表示返回的fileID('\0'结束)
    下载(action==2)：返回的char* 表示下载文件的缓存的首地址(长度为strLen)
    删除(action==3)：返回的char* ("delete success"表示删除成功，"delete failed"表示删除失败)
 
 
 
 
 功能测试：
 系统功能测试的demo程序位于: ./server/DFSClient/clientMain.c
 
没有参数验证时：
上传测试：./client -h 127.0.0.1 -a 1 -u haidong.wang -i group1/M01/05/5F/ChMTFlhspNSADAHZAAcV_Ha0SRA3946051***haidong.wang -p /home/ubuntu/git/DFS/data/terrain.jpg -q 8
下载测试：./client -h 127.0.0.1 -a 2 -u haidong.wang -i group1/M01/05/6A/ChMTFlh4r6iAGwsyAAHTyxac36g7283155***haidong.wang -p /home/ubuntu/git/DFS/data/terrain.jpg -d /home/ubuntu/git/DFS/data/download/terrainSaveInClient.jpg -q 8
删除测试：./client -h 127.0.0.1 -a 3 -u haidong.wang -i group1/M01/05/5F/ChMTFlhspNSADAHZAAcV_Ha0SRA3946051***haidong.wang -p /home/ubuntu/git/DFS/data/terrain.jpg -d /home/ubuntu/git/DFS/data/download/terrainSaveInClient.jpg -q 8
上传2G大文件: ./client -h 127.0.0.1 -a 1 -u haidong.wang -i group1/M01/05/5F/ChMTFlhspNSADAHZAAcV_Ha0SRA3946051***haidong.wang -p /home/ubuntu/git/data/cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb -q -1
返回 group1/M01/05/6A/ChMTFlh5jGeAKDM_eAHHLmhYJTE7444628***haidong.wang 发现服务端的文件缓冲没有释放
group1/M01/05/6A/ChMTFlh5kRWAOenPeAHHLniUBL04981588***haidong.wang

增加参数验证
增加保存fileID和文件全路径的对应关系
服务端和客户端都位于ubuntu
./client -h 127.0.0.1 -a 1 -u haidong.wang -p /home/ubuntu/git/DFS/data/terrain.jpg -f /home/ubuntu/git/DFS/data/fileID_fullPath.txt -q -1
./client -h 127.0.0.1 -a 2 -u haidong.wang -i group1/M01/0F/AD/ChMTF1h5wqGALoyyAAca_BkFcpw1944665***haidong.wang -d /home/ubuntu/git/DFS/data/download/saved.jpg -q -1
./client -h 127.0.0.1 -a 3 -u haidong.wang -i group1/M01/0F/AD/ChMTF1h5sSSAKfqwAAca_ECu8jY3620560***haidong.wang
 
 部署到服务器上(22)，客户端位于ubuntu
 ./client -h 10.19.19.22 -a 1 -u haidong.wang -p /home/ubuntu/git/DFS/data/terrain.jpg -f /home/ubuntu/git/DFS/data/fileID_fullPath.txt -q -1
 ./client -h 10.19.19.22 -a 2 -u haidong.wang -i group1/M01/0F/AD/ChMTF1h5wqGALoyyAAca_BkFcpw1944665***haidong.wang -d /home/ubuntu/git/DFS/data/download/saved.jpg -q -1
 ./client -h 10.19.19.22 -a 3 -u haidong.wang -i group1/M01/0F/AD/ChMTF1h5sSSAKfqwAAca_ECu8jY3620560***haidong.wang
 
 部署在服务器上（22），客户端位于10.19.19.23:/data/sdf/DFSClient/DFS/server/DFSClient/bin
 ./client -h 10.19.19.22 -a 1 -u haidong.wang -p /data/sdf/DFSClient/DFS/data/terrain.jpg -f /data/sdf/DFSClient/DFS/data/fileID_fullPath.txt -q -1
 ./client -h 10.19.19.22 -a 2 -u haidong.wang -i group1/M01/0F/AD/ChMTF1h5wqGALoyyAAca_BkFcpw1944665***haidong.wang -d /data/sdf/DFSClient/DFS/data/download/saved.jpg -q -1
 ./client -h 10.19.19.22 -a 3 -u haidong.wang -i group1/M01/0F/AD/ChMTF1h5sSSAKfqwAAca_ECu8jY3620560***haidong.wang
 

下载大文件：
./client -h 127.0.0.1 -a 2 -u haidong.wang -i group1/M01/05/6A/ChMTFlh5jGeAKDM_eAHHLmhYJTE7444628***haidong.wang -d /home/ubuntu/git/DFS/data/download/saved.jpg -q -1
失败：Source and destination overlap in memcpy (fdfs_download_file.c)
原因：分配2G的大内存失败; 原来的downloadTempBuffer指针没有分配内存，造成在接收文件的时候覆盖其他变量的内存


增加平台ID
上传：./client -h 127.0.0.1 -a 1 -u haidong.wang -p /home/ubuntu/git/DFS/data/terrain.jpg -f /home/ubuntu/git/DFS/data/fileID_fullPath.txt -q -1 -m 59748A23C0109D11387CAF69C8255B4A
下载：./client -h 127.0.0.1 -a 2 -u haidong.wang -i group1/M01/0F/AF/ChMTF1iB4LqAaeLTAAca_B2NA841757549***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d /home/ubuntu/git/DFS/data/download/saved.jpg -q -1 -m 59748A23C0109D11387CAF69C8255B4A
删除：./client -h 127.0.0.1 -a 3 -u haidong.wang -i group1/M01/0F/AF/ChMTF1iB4GqASv5CAAca_C2FWzQ3214762***haidong.wang***59748A23C0109D11387CAF69C8255B4A -m 59748A23C0109D11387CAF69C8255B4A

验证IP： ./client -h 327.0.0.1 -a 1 -u haidong.wang -p /home/ubuntu/git/DFS/data/terrain.jpg -f /home/ubuntu/git/DFS/data/fileID_fullPath.txt -q -1 -m 59748A23C0109D11387CAF69C8255B4A
输出：Sorry, no match with IP...


离散上传:
./client -h 127.0.0.1 -a 11 -u haidong.wang -p /home/ubuntu/git/DFS/data/terrain.jpg -f /home/ubuntu/git/DFS/data/fileID_fullPath.txt -q -1 -m 59748A23C0109D11387CAF69C8255B4A
group1/M03/0F/B0/ChMTF1iYTJeAO8CzAAca_FvJs5g9747725***haidong.wang***59748A23C0109D11387CAF69C8255B4A
测试离散上传的下载:
./client -h 127.0.0.1 -a 2 -u haidong.wang -i group1/M03/0F/B0/ChMTF1iYTJeAO8CzAAca_FvJs5g9747725***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d /home/ubuntu/git/DFS/data/download/uploadDiscreteSaved.jpg -q -1 -m 59748A23C0109D11387CAF69C8255B4A
离散上传超大文件：
./client -h 127.0.0.1 -a 11 -u haidong.wang -p /media/ubuntu/000B534C00015058/Install/ubuntukylin-16.10-enhanced-amd64.iso -f /home/ubuntu/git/DFS/data/fileID_fullPath.txt -q -1 -m 59748A23C0109D11387CAF69C8255B4A


server位于10.19.19.22上，client位于ubuntu
上传：
./client -h 10.19.19.22 -a 11 -u haidong.wang -p /home/ubuntu/git/DFS/data/terrain.jpg -f /home/ubuntu/git/DFS/data/fileID_fullPath.txt -q -1 -m 59748A23C0109D11387CAF69C8255B4A
下载：
./client -h 10.19.19.22 -a 2 -u haidong.wang -i group1/M01/0F/AF/ChMTF1iB4LqAaeLTAAca_B2NA841757549***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d /home/ubuntu/git/DFS/data/download/saved.jpg -q -1 -m 59748A23C0109D11387CAF69C8255B4A
删除：
./client -h 10.19.19.22 -a 3 -u haidong.wang -i group1/M01/0F/AF/ChMTF1iB4GqASv5CAAca_C2FWzQ3214762***haidong.wang***59748A23C0109D11387CAF69C8255B4A -m 59748A23C0109D11387CAF69C8255B4A


server位于10.19.19.22上，client位于10.19.19.23
上传：
./client -h 10.19.19.22 -a 11 -u haidong.wang -p ./terrain.jpg -f ./fileID_fullPath.txt -q -1 -m 59748A23C0109D11387CAF69C8255B4A
下载：
./client -h 10.19.19.22 -a 2 -u haidong.wang -i group1/M01/0F/AF/ChMTF1iB4LqAaeLTAAca_B2NA841757549***haidong.wang***59748A23C0109D11387CAF69C8255B4A -d ./saved.jpg -q -1 -m 59748A23C0109D11387CAF69C8255B4A
删除：
./client -h 10.19.19.22 -a 3 -u haidong.wang -i group1/M01/0F/AF/ChMTF1iB4GqASv5CAAca_C2FWzQ3214762***haidong.wang***59748A23C0109D11387CAF69C8255B4A -m 59748A23C0109D11387CAF69C8255B4A


测试批量上传
ubuntu并发上传会有失败
上传：(失败了5个；卡卡停停)
当带宽不是瓶颈的时候(465,660 B)：
20      3s
50      13s
100     33s
200     32s
500     66s
1000    65s
下载：
200     3s
500     8s
1000    16s
删除：（出现内存泄漏）
500     4s
1000    7s
RES：1272 - 1612(1.277g) ;VIRT: 90,308
CPU峰值：7%


需求设计：
大文件的切分于合并，切分的块数不是越多越好

提供HTTP服务

删除中间层，将中间层功能放置到客户端或者storage上





检查malloc、free对


测试报告：
Use of uninitialised value of size 8
Conditional jump or move depends on uninitialised value
==22475==    by 0x404D97: runserv (server.c:155)

server.c
free(uploadFileBuffer);     // 释放申请的文件缓冲内存!!!
free(fileIDReturnByUpload); // 这个char[]是放在fdfs_upload_file.c中申请


安全验证放置在客户端和服务端 
 
 
 
 
功能完善：
随机生成平台ID（对应于平台token，用于验证），加入fileID之中；并加入到接口当中
生上传文件到Server，再上传到FastDFS前判断platformID和userName是否合法(xxx)  --> 应该先判断上传是否合法，再上传至Server

客户端端口号可配置
增加用户验证（密码）
边读边发、边收边写

Client 常量conf文件限制 
服务只对指定IP开放 Token验证
参数提示信息 具体参数
内存分配失败 异常情况处理
一次性发数据过度

Server
日志 https://github.com/HardySimpson/zlog
http://www.pureage.info/2013/12/31/log-of-fastdfs.html
主进程 Nginx一个进程对应多个线程
参数校验 主进程
前置参数验证，用户（密码）、权限控制
HTTP服务
返回的的是需要url(IP地址加上没有用户名的fileID)还是fileID(有用户名)

修改Eclipse运行程序的当前路径为可执行程序所在的目录
服务端的多线程接收(线程池)
解决单点故障, 发现不可用自动切换到备份服务器
增强访问权限控制(目前为连接加密), 设置可以访问FastDFS的仅仅为中间层程序 

图片处理：https://github.com/libjpeg-turbo/libjpeg-turbo
https://github.com/LuaDist/libjpeg

****************************************************
内存池:
http://www.oschina.net/code/snippet_1987090_44422
https://github.com/wgfxcu/libstpool
****************************************************
 
 
 http://marketplace.eclipse.org/content/texlipse
 
 
 zlog: 
 http://blog.csdn.net/yangzhenzhen/article/details/8439459
 
 
 
 
 group1/M01/0F/AE/ChMTF1iASwaARmncAAca_CYdAgg0188507***haidong.wang
 
 
 
 
 
 
 
 