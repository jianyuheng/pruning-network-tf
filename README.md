# pruning-network-tf
Reproduce some new algorithms of pruning network via TensorFlow.

## 模型压缩三要素： 
1. Model size 模型大小 
2. Run-time memory  模型得小，效率也得高，不能参数少，运算却很多，还是不行滴。 
3. Number of computing operations

## 模型压缩存在的不足： 
1. 低秩分解方法：对全连接层效果可以，对卷积层不怎么样；模型大小可压缩3倍，但运算速度无明显提升。 
2. Weight Quantization: HashNet 虽然可采用分组、共享权值方法来压缩所需保存的参数数量，但是在 Run-time memory上面没有任何压缩。 
3. 二值化权值： 损失精度 
4. Weight Pruning/Sparsifying: 需要专用的硬件或者代码库；训练过程中，没有一个对稀疏进行“约束”“指导”（guidance） 
5. Structured Pruning/Sparsifying

## network slimming
1. 对BN层参数使用L1正则化训练
2. 将BN层参数排序，取中间值，计算Mask，计算掩膜后的结果
3. 计算非0参数值，重新初始化网络结构，并将用之前训练的参数值初始化新的网络
4. 用原数据集微调
