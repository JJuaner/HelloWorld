线性模型：线性回归，线性分类（区别：输出连续的值，定义01离散，多一步非线性映射）
线性回归：g（xw+b）拟合数据
*股票预测：线性回归，多元线性回归（2-最小二乘法）（3-神经元学习算法：随机学习，梯度下降）*
*水果二分类问题，多分类（多个神经元，输出onehot向量）*
最小二乘法最小均方误差 min(wx+b-y)求导=0推导/wb结论


神经网络的矩阵表示
多数入-一个神经元：三XW|=y|
多输入-多神经元：三WX|||=Y|||

MP神经元（wx，阈值函数，01）/感知机神经元（求和wx+b|f，不定）/FT神经元
输入输出
手工设计模型参数-正确输入输出
神经元自动学习参数-正确输入输出

注意输入输出01！！！！！！！
MP阈值函数/b01阶跃函数
and 112
or 111 
not -10
XR 相异为1相同为0 表达式<=>神经网络


3
输入输出-手工设计模型参数输入输出
神经元自动学习参数
神经元学习：有监督（过程描述）/无监督学习（潜在统计信息）
1）调整权重的方法：1.随机 2.hebb（•两个神经元之间的权值变换是与它们神经元的输出成比例的：βxy）3.梯度下降法（梯度，下降）(•梯度的方向就是函数之变化最快的方向)
*感知机有监督分类器/线性回归问题：Hebb学习 βxE(t-y)*
2）学习率调整方法（lr随时间/轮次t的二维变化）：1.学习率衰减（分段常数/逆时/指数/自然指数） 2.学习率预热 3.周期学习率 4.自适应学习率

梯度下降的问题：1.局部最小点（逃离局部最小点：不同初始化，多个初始点搜索/模拟退火思想以一定概率接受更差的结果/随机扰动遗传算法） 2.学习率设置（学习率大小变化，不同参数相同学习率）

4单个神经元学习拟合能力有限，多个神经元万能定理：神经元的连接
层级结构（层内不连，层间全连接，感知机，BP）和互联网型（马尔科夫链：HN，BM）
CNN（本质：带有卷积计算的BP/结构/滑动窗口，权值共享）RNN（循环，反馈）
神经元的扩展：单一神经元（线性回归，二分类）-->宽度（多维多输出单层感知机，多分类多个决策边界），深度（多层感知机，含有隐层，非线性拟合能力更强训练更难）
*多层感知机sinx的拟合：采样数据，手工搭建并设置单隐藏层网络模型（relu，逐点拟合）*密采样
多层感知机的训练：BP算法（梯度下降，链式法则反向传播）
单样本BP算法缺点：样本顺序敏感，
累计BP：收敛慢
动量BP:
5
BP算法计算 
6
优化
1.问题
数据（数据量，数据不同维度差异，正负样本不均衡）
模型（欠拟合，过拟合，泛化能力：定性定量偏差方差）
训练（梯度消失梯度爆炸

2.解决
特征工程：特征选择（选择任务有关特征），性能和复杂度的权衡

正则化：限制模型复杂度，防止过拟合，提高泛化能力
正则化方法：1.数据增强/早停 2权重衰减/dropout 3Lp正则化项（加上参数的Lp范数：系数*|/2----求导后效果：1：容易为0稀疏化 2权重更小

归一化：
原因：不同维度量纲不同，使得分布输入一致，
方法：最大最小 均值方差归一
BN批归一化：对网络中间层对一批数据归一化，激活函数之前
层归一化：对所有层的输入进行归一化
实例归一化：对某些特征归一化
组归一化：把特征通道化为组。组内归一化
可转换归一：结合起来
流程：批均值，批方差，归一，变换（why，归一化后特征损失，恢复数据）

网络参数初始化（局部最小点，考虑2，梯度消失梯度爆炸
不通用（避免对称初始化，对于神经元
权重初始化：4+网络预训练（可复用，更好更快）（有监督，无监督：玻尔兹曼机，自编码器）
偏置初始化：全0，除非输出层偏置

7
神经动力学（系统随时间）
hopfiled网络：确定性神经动力学，反馈神经网络（输出经过其他神经元反馈给自己）
网络结构：神经元二值（激活函数阶跃/符号），单层全互联，对称互联，自己无连
网络运行（状态演化，能量函数必然减小(证明)，直到稳定状态即网络输出，不是训练）：串行并行 uvE的计算
（神经网络和动力学的关系）能量函数计算方法
hopfiled网络的应用：1.局部最小点：联想记忆  2.全局最小点：最优化问题（问题变量对应网络状态，代价函数对应能量函数）
记忆能力：吸引子（网络局部最小点稳定状态，能量函数极值点），
联想：输入状态演化，收敛到吸引子的过程（吸引域，容错联想能力）

8
确定性方法：（确定性的过程和解，能量必然下降）
非确定性方法/统计方法：网络依概率运行
基本思想：基本流程+1随机选取权重2随机修改3调整后保留或者拒绝
修改量！修改量由大变小，与网络能量有关：模拟退火
能量与温度：处于能量E的概率P(E)与温度的关系T（高温中温低温）
模拟退火的基本思路：metropoils和退火（在采样过程中达到 稳定，降温）

玻尔兹曼机=hopfiled+模拟退火（随机神经网络，非确定性神经网络，统计方法）（以一定概率接受，逃离局部最下点）
hopfiled的模型设置
模拟退火的优点思想和运行过程
玻尔兹曼机的运行：
玻尔兹曼机的学习：主动学习，被动学习，调整

T参数的控制：初始值足够高（经验，若干倍，方差） 下降足够慢，终止温度（经验，若干温度不在下降


-------------------------------

（网络需要考虑的问题，提高效果优化）超参数：
数据（密采样增强数据量，归一化）模型复杂度泛化能力
模型：神经元种类/激活函数/个数/层数  
学习：初始化预训练，损失函数，优化方法，学习率，循环控制（迭代次数+损失精度）
训练问题：局部最小点，梯度消失，梯度爆炸，过拟合欠拟合

•单层感知器无法应对非线性的问题，具有单隐层的神经网络可以拟合任意函数。
输入层（0层），输出层（层号=n级网络，Wj），隐藏层（隐藏层：除输入层和输出层以外的其它各层叫隐藏层。 隐藏层不直接接受外界的信号，也不直接向外界发送信号）

sigmoid：1/1+exp(-u) 导数：o(1-o) 图像


----------------------------------------------------------------------

MP神经元（wx，阈值函数，01）/感知机神经元（求和wx+b|f，不定）/FT神经元
输入输出
手工设计模型参数-正确输入输出
神经元自动学习参数-正确输入输出
注意输入输出01！！！！！！！
MP阈值函数/b01阶跃函数
and 112
or 111 
not -10
XR 相异为1相同为0 表达式<=>神经网络

训练过程/BP算法过程:
取样本
前向过程计算网络输出
计算误差
反向过程调整更新参数(梯度下降，链式法则反向传播)
net o 1/2(t-o)2
求L相对于目标参数的梯度（自然链式法则）下降

非线性动力学->网络，反馈，能量函数hopfield
非确定性网络：依据概率接受，允许变坏，逃离局部最小

模型设置
初始化、
训练方法：取样本，前馈，计算误差，反馈
反馈过程的不同：确定性梯度下降，非确定性随机

