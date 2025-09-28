

# word
[在指定位置插入endnote文献列表](https://www.likecs.com/show-204025792.html)


# excel
如何快速比较excel中两列数据中的相同数据、不同数据（A列和B列做对比），如果需要，将上述相同或不同数据提取出来

在C1输入公式
```shell
=MATCH(A1,B:B,)
```

回车后下拉公式，如果返回的是数字，比如说C1的3，就说明A1单元格的内容再B列里第3行存在，也就是B3="A"。如果A列的内容再B列里没有就返回错误值#N/A


# 学术
Google提示your computer or network may be sending automated queries

谷歌学术屏蔽了Vultr 日本和 DO新加坡机房的IP，不要选这两个地方，更换成美国的即可。


LSTM -> Transformer（BERT）
1. 使用多个不同序列同时进行预测，输出加Attention机制（对不同序列自适应加不同的权重）
2. 每个序列最后一个节点的隐含值作为整个序列的特征（或者序列的每个节点加入注意力机制）
3. 使用分离的序列建模不同频率的序列数据，然后合并进行预测。
4. 共享参数，多个序列都输入同一个模型，共同学习特征（多任务学习）
5. 使用效果更好的Transformer或BERT代替LSTM

频率不同复制到频率最大的 -->　单独不同的序列预测 --> 最后接attention机制。

Normal.dotm目录：（快捷键保存目录）
C:\Users\DELL\AppData\Roaming\Microsoft\Templates


没发现大的问题，有两个表述上的可以改下
p11：一般流程是先决策再控制
p28：评论者的英文一般为大写为Actor-Critic
		和后面评论者(Critic)一致：行动者(Actor)


打印机：名字包含258