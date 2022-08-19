# Problems

当 learning rate 较大时($> 10^{-4}$)观察到以下几个现象：

1. 开始时loss下降，但是训练到一定程度时继续训练loss不减反增
2. 一段时间后loss再次下降且下降较为缓慢，训练足够多的epoch后loss完全不变
3. gamma越小loss前期的波动越多，但足够多的epoch后loss还是会完全不变

以下为示例：()
$lr = 10^{-2}$， gamma = 100:
![loss1](/home/wangzixiao/learning/NICD/results/loss1.png)
![result1](/home/wangzixiao/learning/NICD/results/result1.png)

$lr = 10^{-2}$， gamma = 10:
![loss2](/home/wangzixiao/learning/NICD/results/loss2.png)
![result2](/home/wangzixiao/learning/NICD/results/result2.png)

$lr = 10^{-2}$， gamma = 1:
![loss3](/home/wangzixiao/learning/NICD/results/loss3.png)
![result3](/home/wangzixiao/learning/NICD/results/result3.png)

$lr = 10^{-3}$， gamma = 100:
![loss4](/home/wangzixiao/learning/NICD/results/loss4.png)
![result4](/home/wangzixiao/learning/NICD/results/result4.png)

$lr = 10^{-4}$， gamma = 100:
![loss5](/home/wangzixiao/learning/NICD/results/loss5.png)
![result5](/home/wangzixiao/learning/NICD/results/result5.png)

当做优化时，降低loss的方法除了最大化 k(X, Y).mean() 之外还有 最小化 k(X, X).mean()， 这也是为什么到了一定程度之后loss不下降的原因：新生成的样本中所有的X数值都相当大，导致rbf_kernel在X的每两个值之间都是0，此时达到最优。看看能不能换一个kernel或者更改一下loss function 使得生成出来的数据必须和目标分布在同一个数值范围内
