

https://github.com/Ravenbrook/mps
https://github.com/WangLiangCN/Memory-Pool
https://github.com/dcshi/ncx_mempool

MPS
cd code
make -f lii6ll.gmk  在目录下产生lii6ll文件夹，里面有cool和hot

安装：
./configure --prefix=~/mps
make install

内核中有不少地方内存分配不允许失败
内核中内存池真实地只是相当于后备缓存
简洁但不简单
这是个随手扔垃圾还是扔到垃圾袋再扔垃圾桶哪个更好的问题。
随处一扔幻想着有一个伟大的函数可以像妈妈一样呵护你