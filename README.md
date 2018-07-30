# pruning-network-tf
Reproduce some new algorithms of pruning network via TensorFlow.

## network slimming
1. 对BN层参数使用L1正则化训练
2. 将BN层参数排序，取中间值，计算Mask，计算掩膜后的结果
3. 计算非0参数值，重新初始化网络结构，并将用之前训练的参数值初始化新的网络
4. 用原数据集微调
