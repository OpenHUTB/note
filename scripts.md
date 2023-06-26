




获得父进程的pid：get_ppid.sh
function ppid () {
   ps -p ${1:-$$} -o ppid=;
}
pid=$1
if [ -z $pid ]
then
       read -p "PID: " pid
   fi 
   ps -p ${pid:-$$} -o ppid=
调用：sh get_ppid.sh 20118
-z代表的是该变量是否有值。
-d代表的是判断制定的是否是一个目录
ps -p ${20118:-$$}
$$ 这个程式的PID(脚本运行的当前进程ID号)
${1:-}的意思就是说，如果函数有第一个参数，就返回这个参数，如果没有，就返回空
-o : format


************************************************************************************
批量构造文件copy_multi.sh
for ((i=1;i<=60;i++))
do
        for x in ./data_000001/*
        do
                var=$(cat /proc/sys/kernel/random/uuid);
                cp $x ./data_000001/$var.jpg
        done
done

************************************************************************************

sed -i '2056,2076 s/^/;/g' /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php_test.ini

releasePHP.sh
sed -i '2056,2076 s/^/;/g' /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php.ini
ps aux | grep php-fpm | grep wanghai | awk '{print $2}' | xargs kill -s 9
/home/wanghaidong/AP2/softwares/php-5.6.30/sbin/php-fpm

debugPHP.sh
sed -i '2056,2076 s/^;//g' /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php.ini
ps aux | grep php-fpm | grep wanghai | awk '{print $2}' | xargs kill -s 9
/home/wanghaidong/AP2/softwares/php-5.6.30/sbin/php-fpm




**********************************************************************************

https://my.oschina.net/musings/blog/380939
批量拉取文件并重命名：
for k in $(seq 1 25)
do

wget http://10.19.19.24/datasys/tool/fastdfs/download/?url=jcarwsoiadbe7srLtA8T0tJO0muY3d8PXdYSZMaP8ZEmQRX4nuHKZUCjTsPZJR8AoApR2KcE5pLRuiEs9%2F0MmmA49%2BkfRqqkZKmlVNedyNSbmSQWuefg5wBa9PAfVs%2Bvwp6mGL4aUvBIWV%2Fqri0aAMhiMwgvlJ0KtuLmt272wPv%2FmmjAXslEuewctz3Cj0FJEM%2BRRNoVVxODNNlEINuMEA%3D%3D -O "1_$k.wav"

wget http://10.19.19.24/datasys/tool/fastdfs/download/?url=M%2Bujq8eerc4z3Uh0jOy3N2dhKkYk28MKiTsUPMMcsFKvl4Tt0la3PHFT3pdcVdry6QVfBNLVz1AsO6fjbtQm%2FyzJYAi1ruftXuudHuK233AwnG92QexJY4FqK0KENXjvjq6tllXG0k3VeAUWgb64UOIl%2F7OuEgsoikZ3gNqO8gu6T9Gmkhp4M3Xsdd4lOR3bUz8qbFeFUInSTGcUk70jdQ%3D%3D -O "2_$k.wav"

wget http://10.19.19.24/datasys/tool/fastdfs/download/?url=SIDai%2BNIjmjUlUAIBbzUybtx4iYItX4LQc%2FNKWiIPnQ%2BEncVkhV9n42lZceK1bfxpfGaOBZl5llQd1lFZIkR%2B92jOxlAm5phSCZv0vOZTtBYSWgXftkM34DO0vk%2FvMppsPkC66LaudtXstHuOAfsX8FrjKfOF9j8nF0Qd3yDdvP8RCDXj3Ln%2FmHD68b35%2BpeivPbCQ6bgXS9ajcC46ZN1A%3D%3D -O "3_$k.wav"

wget http://10.19.19.24/datasys/tool/fastdfs/download/?url=vj9WhuMV6m%2FAEhNJNrpGcq7Tfq0E9BMzw5r5WJCxoSHA7KoElp75X6OMlCOAZq1cbW%2BplaKlT10r49h2oWSuDyExh1ylWl9gV9gmrSnHW5TuRZACSZC13yttqS3F6mcmK5ZMI2pifXkQI3M%2Bsy%2BKR4%2BSsyE%2Fq4vt0cLCcHbKM6KPS6xsTLKFO9yux1KXcUupEaMidw5YgqSvhmXLHDd7%2Fw%3D%3D -O "4_$k.wav"

done