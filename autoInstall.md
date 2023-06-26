
中断之前
http://10.19.19.22:8080/action.php?fileID=GQwRCw5PUTNOT1FGSFFLPFE9FjMqOBIVRkwqUz80ITEIPz8PEjoUPw87PRVGRkhLSEhJ&dueTime=T0pHRkxJSU9HRg==


上传：group1/M03/00/00/ChMTGFlN_m6AfVFiAAca_EYe81k3324803***haidong.wang***59748A23C0109D11387CAF69C8255B4A
有效链接（24）
http://10.19.19.24:8080/action.php?fileID=GQwRCw5PUTNOTVFOTlFOTlE9FjMqOTgSMCETSD8YKDgXPz8dHyE7JxtGTxVNTUxKRk5N&dueTime=T0pHRk1KTUZGSQ==

简化安装
group1/M00/89/24/ChMTFllMzqGAK_yJAAAGSXKR7FI74.conf
http://10.19.19.24:8080/group1/M00/94/15/ChMTF1lM2kKATFW3AFZbolrzCb0875.bmp
http://10.19.19.23:8080/action.php?fileID=GQwRCw5PUTNOTVFHTVFNP1E9FjMqOE8SNEcmOT8wUyEnPz86F0tNTR9LGxVLSEhJR0dP&dueTime=T0pHRkxPTUhNTg==?1498211833715
\

test
test1/M00/00/00/ChMTF1lNETSAa67ZAFZbontJus0934.bmp
http://10.19.19.23:8093/test1/M00/00/00/ChMTF1lNETSAa67ZAFZbontJus0934.bmp

DESTDIR="/data/sdb/group1_3/"

tar xf software_fastdfs.tar
cd softwares
tar xf fastdfs-5.05.tar
tar xf libfastcommon-1.0.7.tar
tar zxf pcre-8.36.tar.gz
tar zxf fastdfs-nginx-module_v1.16.tar.gz
tar zxf nginx-1.7.9.tar.gz
tar zxf zlib-1.2.8.tar.gz

# install libfastcommon-1.0.7
cd libfastcommon-1.0.7/src
sed -i '1aDESTDIR=$1' Makefile.in
# sed -i '48a\  $(warning $(DESTDIR))' Makefile.in      # 对tab进行转义，并打出变量值）
sed -i 's/\/usr\/lib64/${DESTDIR}libfastcommon-1.0.7\/lib/' Makefile.in
sed -i 's/\/usr\/include\/fastcommon/${DESTDIR}libfastcommon-1.0.7\/include/' Makefile.in
cd ..
./make.sh
./make.sh install DESTDIR=${DESTDIR}    #传递给Makefile参数DIR=***
cd ..

# install fastdfs-5.05
cd fastdfs-5.05







INSTALL_DIR="/data/sdb/group1_3/"

tar xf software_fastdfs.tar
cd softwares
tar xf fastdfs-5.05.tar
tar xf libfastcommon-1.0.7.tar
tar zxf pcre-8.36.tar.gz
tar zxf fastdfs-nginx-module_v1.16.tar.gz
tar zxf nginx-1.7.9.tar.gz
tar zxf zlib-1.2.8.tar.gz

# install libfastcommon-1.0.7
cd libfastcommon-1.0.7/src
sed -i '1aINSTALL_DIR=$1' Makefile.in
sed -i '48a\    $(warning $(INSTALL_DIR))' Makefile.in  # 对tab进行转义，并打出变量值）
sed -i 's/\/usr\/lib64/${INSTALL_DIR}libfastcommon-1.0.7\/lib/' Makefile.in
sed -i 's/\/usr\/include\/fastcommon/${INSTALL_DIR}libfastcommon-1.0.7\/include/' Makefile.in
cd ..
./make.sh
./make.sh install INSTALL_DIR=${INSTALL_DIR}    #传递给Makefile参数DIR=***
cd ..

# install fastdfs-5.05
cd fastdfs-5.05
cd tracker
sed -i '1aINSTALL_DIR=$2' Makefile.in
sed -i '5s/$/&\ -I${INSTALL_DIR}libfastcommon-1.0.7\/include/' Makefile.in
sed -i '6s/$/&\ -L${INSTALL_DIR}libfastcommon-1.0.7\/lib/' Makefile.in
#sed -i '8a$(warning $(INSTALL_DIR))' Makefile.in
cd ..

cd storage
sed -i '1aINSTALL_DIR=$2' Makefile.in
sed -i '5s/$/&\ -I${INSTALL_DIR}libfastcommon-1.0.7\/include/' Makefile.in
sed -i '6s/$/&\ -L${INSTALL_DIR}libfastcommon-1.0.7\/lib/' Makefile.in
cd ..

cd client
sed -i '1aINSTALL_DIR=$2' Makefile.in
sed -i '7s/$/&\ -I${INSTALL_DIR}libfastcommon-1.0.7\/include/' Makefile.in
sed -i '8s/$/&\ -L${INSTALL_DIR}libfastcommon-1.0.7\/lib/' Makefile.in
cd ..

cd test
sed -i '1aINSTALL_DIR=$2' Makefile.in
sed -i '5s/$/&\ -I${INSTALL_DIR}libfastcommon-1.0.7\/include/' Makefile.in
sed -i '6s/$/&\ -L${INSTALL_DIR}libfastcommon-1.0.7\/lib/' Makefile.in
cd ..

sed -i 's/$1\ $2/$2/' make.sh
sed -i '1aDESTDIR=$1' make.sh

./make.sh DESTDIR=${INSTALL_DIR}fastdfs-5.05 INSTALL_DIR=${INSTALL_DIR}
./make.sh install








