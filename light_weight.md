
已经训练好的模型上进行处理；
轻量化卷积神经网络：SqueezeNet、MobileNet、ShuffleNet、Xception
在卷积方式上做了改变

squeeze 在 SqueezeNet 中表示一个 squeeze 层，该层采用 1*1 卷积核对上一层 feature map 进行卷积，
主要目的是减少 feature map 的维数（维数即通道数，就是一个立方体的 feature map，切成一片一片的，一共有几片）。

shuffle 具体来说是 channel shuffle，是将各部分的 feature map 的 channel 进行有序的打乱，构成新的 feature map，
以解决 group convolution 带来的「信息流通不畅」问题。
（MobileNet 是用 point-wise convolution 解决的这个问题）

