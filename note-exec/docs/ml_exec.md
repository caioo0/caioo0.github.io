# 吴恩达机器学习习题90题 
---
## Week 1 | 1 介绍

> 来源：https://www.heywhale.com/mw/notebook/64e5aa273852baaea396f6be
> 课程：https://www.coursera.org/learn/machine-learning/

### 第 1 题

一个计算机程序从经验E中学习任务T，并用P来衡量表现。并且，T的表现P随着经验E的增加而提高。
假设我们给一个学习算法输入了很多历史天气的数据，让它学会预测天气。什么是P的合理选择？

A. 计算大量历史气象数据的过程  
B. 以上都不  
C. 正确预测未来日期天气的概率  
D. 天气预报任务  

### 第 2 题

假设你正在做天气预报，并使用算法预测明天气温（摄氏度/华氏度），你会把这当作一个分类问题还是一个回归问题？

A. 分类  ✔ 
B. 回归   

### 第 3 题

假设你在做股市预测。你想预测某家公司是否会在未来7天内宣布破产（通过对之前面临破产风险的类似公司的数据进行训练）。你会把这当作一个分类问题还是一个回归问题？

A. 分类   
B. 回归   

### 第 4 题

下面的一些问题最好使用有监督的学习算法来解决，而其他问题则应该使用无监督的学习算法来解决。以下哪一项你会使用监督学习？（选择所有适用的选项）在每种情况下，假设有适当的数据集可供算法学习。

A. 根据一个人的基因（DNA）数据，预测他/她的未来10年患糖尿病的几率   
B. 根据心脏病患者的大量医疗记录数据集，尝试了解是否有不同类患者群，我们可以为其量身定制不同的治疗方案    
C. 让计算机检查一段音频，并对该音频中是否有人声（即人声歌唱）或是否只有乐器（而没有人声）进行分类  
D. 给出1000名医疗患者对实验药物的反应（如治疗效果、副作用等）的数据，发现患者对药物的反应是否有不同的类别或“类型”，如果有，这些类别是什么   

### 第 5 题

哪一个是机器学习的合理定义？

A. 机器学习从标记的数据中学习

B. 机器学习能使计算机能够在没有明确编程的情况下学习

C. 机器学习是计算机编程的科学

D. 机器学习是允许机器人智能行动的领域

## 1-5题 答案 & 题解

1.C 2.B 3.A 4.母鸡 5.B
文科题要啥题解

## Week 1 | 2 单变量线性回归

### 第 6 题

基于一个学生在大学一年级的表现，预测他在大学二年级表现。
令x等于学生在大学第一年得到的“A”的个数（包括A-，A和A+成绩）学生在大学第一年得到的成绩。预测y的值：第二年获得的“A”级的数量
这里每一行是一个训练数据。在线性回归中，我们的假设ℎ(x)=y_0+1，并且我们使用m来表示训练示例的数量。

```
| x    | y    |  
| 3    | 2    |  
| 1    | 2    |  
| 0    | 1    |  
| 4    | 3    |  
  
```

对于上面给出的训练集（注意，此训练集也可以在本测验的其他问题中引用），m的值是多少？

### 第 7 题

对于这个问题，假设我们使用第一题中的训练集。并且，我们对代价函数的定义是�(�0,�1)=12�∑�=1�(ℎ�(�(�))−�(�))2
求�(0,1)

### 第 8 题

令问题1中，线性回归假设的�0=−1,�1=2，求ℎ�(6)？

### 第 9 题

代价函数�(�0,�1)与�0,�1的关系如图2所示。“图1”中给出了相同代价函数的等高线图。根据图示，选择正确的选项（选出所有正确项）

![Image Name](https://cdn.kesci.com/upload/image/q3o1ai1t0.png?imageView2/0/w/960/h/960)

A. 从B点开始，学习率合适的梯度下降算法会最终帮助我们到达或者接近A点，即代价函数�(�0,�1)在A点有最小值

B. 点P（图2的全局最小值）对应于图1的点C

C. 从B点开始，学习率合适的梯度下降算法会最终帮助我们到达或者接近C点，即代价函数�(�0,�1)在C点有最小值

D. 从B点开始，学习率合适的梯度下降算法会最终帮助我们到达或者接近A点，即代价函数�(�0,�1)在A点有最大值

E. 点P（图2的全局最小值）对应于图1的点A

### 第 10 题

假设对于某个线性回归问题（比如预测房价），我们有一些训练集，对于我们的训练集，我们能够找到一些�0,�1，使得�(�0,�1)=0。
以下哪项陈述是正确的？（选出所有正确项）

A. 为了实现这一点，我们必须有�0=0,�1=0，这样才能使�(�0,�1)=0

B. 对于满足�(�0,�1)=0的�0,�1的值，其对于每个训练例子(�(�),�(�))，都有ℎ�(�(�))=�(�)

C. 这是不可能的：通过�(�0,�1)=0的定义，不可能存在�0,�1使得�(�0,�1)=0

D. 即使对于我们还没有看到的新例子，我们也可以完美地预测y的值（例如，我们可以完美地预测我们尚未见过的新房的价格）

## 6-10题 答案 & 题解

6.4
7.0.5
代进去算一下就行了
�(0,1)=12∗4((3−2)2+(1−2)2+(0−1)2+(4−3)2)=0.5

8.11
也是代进去算下就行了
ℎ�(6)=−1+2∗6=11

9.AE
P是全局最小值，对应的是A

10.B
A: ℎ�(�)=0，不等于�(�0,�1)=0
B: 当完全拟合时,就会出现损失函数为0的情况，正确
C: B与C说法正好相反. 当完全拟合时,就会出现损失函数为0的情况
D: 不行

## Week 1 | 3 线性代数

### 第 11 题

定义2个矩阵

�=[4369],�=[−29−52]


那么A-B是多少？



A.

[41211]


B.

[6−121111]



C.

[2−617]



D.

[6−6117]



### 第 12 题

令

�=[2741]


那么12∗�是多少



### 第 13 题

令�是一个3维向量，并且

�=[519]


那么��是多少



### 第 14 题

令�,�为3维向量，并且

，�=[12−1]，�=[224]


那么���是多少？



### 第 15 题

令A和B是3x3矩阵，以下哪一项一定是正确的（选出所有正确项）

A. �+�=�+�
B. 如果�是一个3维向量，那么�∗�∗�是三维向量
C. �∗�∗�=�∗�∗�
D. 如果�=�∗�，那么�是个6x6矩阵

## 11-15题 答案 & 题解

11.D
12.

[172212]


13.

[519]


14.2
15.AB



## Week 2 | 1 多元线性回归

### 第 16 题

假设m=4个学生上了一节课，有期中考试和期末考试。你已经收集了他们在两次考试中的分数数据集，如下所示：

| 期中得分 | (期中得分)^2 | 期末得分 |
| :------- | :----------- | :------- |
| 89       | 7921         | 96       |
| 72       | 5184         | 74       |
| 94       | 8836         | 87       |
| 69       | 4761         | 78       |

你想用多项式回归来预测一个学生的期中考试成绩。具体地说，假设你想拟合一个ℎ�(�)=�0+�1�1+�2�2的模型，其中x1是期中得分，x2是（期中得分）^2。此外，你计划同时使用特征缩放（除以特征的“最大值-最小值”或范围）和均值归一化。

标准化后的�2(4)特征值是多少？（提示：期中=89，期末=96是训练示例1）

### 第 17 题

用�=0.3进行15次梯度下降迭代，每次迭代后计算�(�)。你会发现�(�)的值下降缓慢，并且在15次迭代后仍在下降。基于此，以下哪个结论似乎最可信？

A. �=0.3是学习率的有效选择。

B. 与其使用�当前值，不如尝试更小的�值（比如�=0.1）

C. 与其使用�当前值，不如尝试更大的�值（比如�=1.0）

### 第 18 题

假设您有m=14个训练示例，有n=3个特性（不包括需要另外添加的恒为1的截距项），正规方程是�=(���)−1���。对于给定m和n的值，这个方程中�,�,�的维数分别是多少？

A. � 14×3, � 14×1, � 3×3
B. � 14×4, � 14×1, � 4×1
C. � 14×3, � 14×1, � 3×1
D. � 14×4, � 14×4, � 4×4

### 第 19 题

假设您有一个数据集，每个示例有m=1000000个示例和n=200000个特性。你想用多元线性回归来拟合参数�到我们的数据。你更应该用梯度下降还是正规方程？

A. 梯度下降，因为正规方程中�=(���)−1中计算非常慢

B. 正规方程，因为它提供了一种直接求解的有效方法

C. 梯度下降，因为它总是收敛到最优�

D. 正规方程，因为梯度下降可能无法找到最优�

### 第 20 题

以下哪些是使用特征缩放的原因？

A. 它可以防止梯度下降陷入局部最优

B. 它通过降低梯度下降的每次迭代的计算成本来加速梯度下降

C. 它通过减少迭代次数来获得一个好的解，从而加快了梯度下降的速度

D. 它防止矩阵���（用于正规方程）不可逆（奇异/退化）

## 16-20题 答案 & 题解

16.-0.47 17.C 18.B 19.A 20.C

## Week 2 | 2 OctaveMatlab 练习

### 第 21 题

假设我首先在Octave/Matlab中执行以下操作：

```
A=[1 2；3 4；5 6]
B=[1 2 3；4 5 6]
```

以下哪项是有效的命令？选出所有正确项（提示：A'表示A的转置）

A. C = A’ + B
B. C = B * A
C. C = A + B
D. C = B’ * A

### 第 22 题

令

�=[16231351110897612414151]


以下那种索引方式可以得到

�=[16251197414]


选出所有正确项



A. B= A(:, 1:2)
B. B = A(1:4, 1:2)
C. B = A(:, 0:2)
D. B = A(0:4, 0:2)

注：matlab的从1开始，python的index从0开始，matlab的索引包含头尾，python的索引含头不含尾

### 第 23 题

令A为10x10矩阵，x为10元素向量。您的朋友想计算乘积Ax并编写以下代码：

```
v = zeros(10, 1);  
for i = 1:10  
  for j = 1:10  
    v(i) = v(i) + A(i, j) * x(j);  
  end  
end  
```

你将如何不用循环，向量化这段代码？选出所有正确项

A. v = A * x
B. v = Ax
C. v = x’ * A
D. v = sum (A * x)

### 第 24 题

假设有两个列向量v和w，每个向量都有7个元素（即，它们的维数为7x1）。请考虑以下代码：

```
z = 0;  
for i = 1:7  
  z = z + v(i) * w(i)  
end  
```

下列哪个矢量化正确计算z？选出所有正确项

A. z = sum (v .* w)
B. z = w’ * v
C. z = v * w’
D. z = w * v’

### 第 25 题

在Octave/Matlab中，许多函数可以处理单个数字、向量和矩阵。例如，将sin函数应用于矩阵时，将返回一个新矩阵，其中包含每个元素的sin。但是你必须小心，因为某些函数有不同的行为。假设你有一个7x7矩阵X，你想计算每个元素的对数，每个元素的平方，每个元素加1，每个元素除以4。将结果存储在四个矩阵（A、B、C、D）中。一种方法是使用以下代码：

```
for i = 1:7  
  for j = 1:7  
    A(i, j) = log(X(i, j));  
    B(i, j) = X(i, j) ^ 2;  
    C(i, j) = X(i, j) + 1;  
    D(i, j) = X(i, j) / 4;  
  end  
end  
```

下列哪一项正确计算A、B、C或D？选出所有正确项
A. C = X + 1;
B. D = X / 4;
C. A = log (X);
D. B = X ^ 2;

## 21-25题 答案 & 题解

21.AB 22.AB 23.A 24.AB 25.ABC

## Week 3 | 1 逻辑回归

### 第 26 题

假设您已经训练了一个逻辑分类器，它在一个新示例x上输出一个预测ℎ�(�)=0.4。这意味着（选出所有正确项）：

A. 我们对�(�=0∣�;�)的估计是0.4

B. 我们对�(�=1∣�;�)的估计是0.6

C. 我们对�(�=0∣�;�)的估计是0.6

D. 我们对�(�=1∣�;�)的估计是0.4

### 第 27 题

假设您有以下训练集，并拟合logistic回归分类器ℎ�(�)=�(�0+�1�1+�2�2)

![Image Name](https://cdn.kesci.com/upload/image/q3oem1y8j3.jpg?imageView2/0/w/960/h/960)

![Image Name](https://cdn.kesci.com/upload/image/q3oem98cp2.jpg?imageView2/0/w/960/h/960)

以下哪项是正确的？选出所有正确项

A. 添加多项式特征（例如，使用ℎ�(�)=�(�0+�1�1+�2�2+�3�12+�4�1�2+�5�22)）可以增加我们拟合训练数据的程度

B. 在�的最佳值（例如，由fminunc找到）处，�(�)≥0

C.添加多项式特征（例如，使用ℎ�(�)=�(�0+�1�1+�2�2+�3�12+�4�1�2+�5�22)将增加�(�)，因为我们现在正在对更多项进行求和

D.如果我们训练梯度下降迭代足够多次，对于训练集中的一些例子�(�)，可能得到ℎ�(�(�))>1

### 第 28 题

对于逻辑回归，梯度由∂∂���(�)=1�∑�=1�(ℎ�(�(�))−�(�))��(�)给出。以下哪项是学习率为�的逻辑回归的正确梯度下降更新？选出所有正确项

A. �:=�−�1�∑�=1�(���−�(�))�(�)

B. ��:=��−�1�∑�=1�(11+�−���(�)−�(�))��(�)（同时更新所有�）

C. ��:=��−�1�∑�=1�(ℎ�(�(�))−�(�))�(�)（同时更新所有�）

D. ��:=��−�1�∑�=1�(ℎ�(�(�))−�(�))��(�)（同时更新所有�）

### 第 29 题

以下哪项陈述是正确的？选出所有正确项

A. 对于逻辑回归，梯度下降有时会收敛到一个局部最小值（并且无法找到全局最小值）。这就是为什么我们更喜欢更先进的优化算法，如fminunc（共轭梯度/BFGS/L-BFGS/等等）

B. sigmoid函数�(�)=11+�−�数值永远不会大于1

C.用�≥1个例子训练的逻辑回归的代价函数�(�)总是大于或等于零

D. 使用线性回归+阈值的方法做分类预测，总是很有效的

### 第 30 题

假设训练一个逻辑回归分类器ℎ�(�)=�(�0+�1�1+�2�2)。假设�0=6,�1=−1,�2=0，下列哪个图表示分类器找到的决策边界？

A.
![Image Name](https://cdn.kesci.com/upload/image/q3oeqa1yek.jpg?imageView2/0/w/960/h/960)

B.

![Image Name](https://cdn.kesci.com/upload/image/q3oeqo1xpd.jpg?imageView2/0/w/960/h/960)

C.

![Image Name](https://cdn.kesci.com/upload/image/q3oeqw5knk.jpg?imageView2/0/w/960/h/960)

D.

![Image Name](https://cdn.kesci.com/upload/image/q3oesexzdg.jpg?imageView2/0/w/960/h/960)

## 26-30题 答案 & 题解

26.CD 27.AB 28.BD 29.BC 30.A

## Week 3 | 2 正则化

### 第 31 题

你正在训练一个分类逻辑回归模型。以下哪项陈述是正确的？选出所有正确项

A. 将正则化引入到模型中，总是能在训练集上获得相同或更好的性能

B. 在模型中添加许多新特性有助于防止训练集过度拟合

C. 将正则化引入到模型中，对于训练集中没有的例子，总是可以获得相同或更好的性能

D. 向模型中添加新特征总是会在训练集上获得相同或更好的性能

### 第 32 题

假设您进行了两次逻辑回归，一次是�=0，一次是�=1。其中一次，得到参数�=[81.4712.69]，另一次，得到�=[13.010.91]。
但是，您忘记了哪个�值对应于哪个�值。你认为哪个对应于�=1？

A. �=[13.010.91]

B. �=[81.4712.69]

### 第 33 题

以下关于正则化的陈述哪一个是正确的？选出所有正确项

A. 使用太大的�值可能会导致您的假设与数据过拟合；这可以通过减小�来避免

B. 使用非常大的值�不会影响假设的性能；我们不将�设置为太大的唯一原因是避免数值问题

C. 考虑一个分类问题。添加正则化可能会导致分类器错误地分类某些训练示例（当不使用正则化时，即当�=0时，它正确地分类了这些示例）

D. 由于逻辑回归的输出值0≤ℎ�(�)≤1，其输出值的范围无论如何只能通过正则化来“缩小”一点，因此正则化通常对其没有帮助

### 第 34 题

下列哪一个图片的假设与训练集过拟合？

A.

![Image Name](https://cdn.kesci.com/upload/image/q3oh2j8ms5.jpg?imageView2/0/w/960/h/960)

B.

![Image Name](https://cdn.kesci.com/upload/image/q3oh2pcz0h.jpg?imageView2/0/w/960/h/960)

C.

![Image Name](https://cdn.kesci.com/upload/image/q3oh2w1vtg.jpg?imageView2/0/w/960/h/960)

D.

![Image Name](https://cdn.kesci.com/upload/image/q3oh34y2z3.jpg?imageView2/0/w/960/h/960)

### 第 35 题

下列哪一个图片的假设与训练集欠拟合？

A.

![Image Name](https://cdn.kesci.com/upload/image/q3oh7rde8b.jpg?imageView2/0/w/960/h/960)

B.

![Image Name](https://cdn.kesci.com/upload/image/q3oh7xnr0x.jpg?imageView2/0/w/960/h/960)

C.

![Image Name](https://cdn.kesci.com/upload/image/q3oh8393qg.jpg?imageView2/0/w/960/h/960)

D.

![Image Name](https://cdn.kesci.com/upload/image/q3oh8dlzjj.jpg?imageView2/0/w/960/h/960)

## 31-36题 答案 & 题解

31.D 32.A 33.C 34.A 35.A

## Week 4 | 1 神经网络的正向传播

### 第 36 题

以下哪项陈述是正确的？选择所有正确项

A. 神经网络中隐藏单元的激活值，在应用了sigmoid函数之后，总是在（0，1）范围内

B. 在二进制值（0或1）上的逻辑函数可以（近似）用一些神经网络来表示

C. 两层（一个输入层，一个输出层，没有隐藏层）神经网络可以表示异或函数

D. 假设有一个三个类的多类分类问题，使用三层网络进行训练。设�1(3)=(ℎΘ(�))1为第一输出单元的激活，并且类似地，有�2(3)=(ℎΘ(�))2和�3(3)=(ℎΘ(�))3。那么对于任何输入x，必须有�1(3)+�2(3)+�3(3)=1

### 第 37 题

考虑以下两个二值输入�1,�2∈{0,1}和输出ℎΘ(�)的神经网络。它（近似）计算了下列哪一个逻辑函数？

![Image Name](https://cdn.kesci.com/upload/image/q3oj8j5iry.png?imageView2/0/w/960/h/960)

A. OR
B. AND
C. NAND (与非)
D. XOR (异或)

### 第 38 题

考虑下面给出的神经网络。下列哪个方程正确地计算了�1(3)的激活？注：�(�)是sigmoid激活函数

![Image Name](https://cdn.kesci.com/upload/image/q3ojbwnojc.jpg?imageView2/0/w/960/h/960)

A. �1(3)=�(Θ1,0(2)�0(2)+Θ1,1(2)�1(2)+Θ1,2(2)�2(2))

B. �1(3)=�(Θ1,0(1)�0(1)+Θ1,1(1)�1(1)+Θ1,2(1)�2(1))

C. �1(3)=�(Θ1,0(1)�0(2)+Θ1,1(1)�1(2)+Θ1,2(1)�2(2))

D. 此网络中不存在激活�1(3)

### 第 39 题

你有以下神经网络：

![Image Name](https://cdn.kesci.com/upload/image/q3ojrt6ije.jpg?imageView2/0/w/960/h/960)

你想计算隐藏层�(2)∈�3的激活，一种方法是使用以下Octave代码：

![Image Name](https://cdn.kesci.com/upload/image/q3ojs6hzmm.jpg?imageView2/0/w/960/h/960)

您需要一个矢量化的实现（即，一个不用循环的实现）。下列哪个实现正确计算�(2)？选出所有正确项

A. z = Theta1 * x; a2 = sigmoid (z)
B. a2 = sigmoid (x * Theta1)
C. a2 = sigmoid (Theta2 * x)
D. z = sigmoid(x); a2 = sigmoid (Theta1 * z)

### 第 40 题

您正在使用下图所示的神经网络，并已学习参数Θ(1)=[112.411.73.2]（用于计算�(2)）和Θ(2)=[10.3−1.2]（用于作用在�(2)的函数，计算�(3)的值）。

假设您交换第一个隐藏层的2个单元的参数Θ(1)=[11.73.2112.4]，并且还交换输出层Θ(2)=[1−1.20.3]。这将如何改变输出ℎΘ(�)的值？

![Image Name](https://cdn.kesci.com/upload/image/q3ok7hvi53.jpg?imageView2/0/w/960/h/960)

A. 不变
B. 变大
C. 变小
D. 信息不全，可能变大也可能变小

## 36-40题 答案 & 题解

36.AB 37.A 38.A 39.A 40.A

## Week 5 | 1 神经网络的反向传播

### 第 41 题

您正在训练一个三层神经网络，希望使用反向传播来计算代价函数的梯度。
在反向传播算法中，其中一个步骤是更新
Δ��(2):=Δ��(2)+��(3)∗(�(2))�
对于每个i，j，下面哪一个是这个步骤的正确矢量化？

A. Δ(2):=Δ(2)+(�(2))�∗�(3)
B. Δ(2):=Δ(2)+(�(3))�∗�(2)
C. Δ(2):=Δ(2)+�(3)∗(�(2))�
D. Δ(2):=Δ(2)+�(3)∗(�(3))�

### 第 42 题

假设`Theta1`是一个5x3矩阵，`Theta2`是一个4x6矩阵。令`thetaVec=[Theta1(;);Theta2(:)]`。下列哪一项可以正确地还原`Theta2`？

A. `reshape(thetaVec(16:39),4,6)`
B. `reshape(thetaVec(15:38),4,6)`
C. `reshape(thetaVec(16:24),4,6)`
D. `reshape(thetaVec(15:39),4,6)`
E. `reshape(thetaVec(16:39),6,4)`

### 第 43 题

设�(�)=2�3+2，设�=1,�=0.01。用公式��(�+�)−�(�−�)2�来数值计算在�=1时的逼近。你将得到什么值？（当�=1时，精确导数为��(�)��=6）

A. 8
B. 6
C. 5.9998
D. 6.0002

### 第 44 题

以下哪项陈述是正确的？选择所有正确项

A. 使用较大的�值不会影响神经网络的性能；我们不将�设置为太大的唯一原因是避免数值问题

B. 如果我们使用梯度下降作为优化算法，梯度检查是有用的。然而，如果我们使用一种先进的优化方法（例如在fminunc中），它没有多大用处

C. 使用梯度检查可以帮助验证反向传播的实现是否没有bug

D. 如果我们的神经网络过拟合训练集，一个合理的步骤是增加正则化参数�

### 第 45 题

以下哪项陈述是正确的？选择所有正确项

A. 假设参数Θ(1)是一个方矩阵（即行数等于列数）。如果我们用它的转置(Θ(1))�代替Θ(1)，那么我们并没有改变网络正在计算的功能。

B. 假设我们有一个正确的反向传播实现，并且正在使用梯度下降训练一个神经网络。假设我们将�(Θ)绘制为迭代次数的函数，并且发现它是递增的而不是递减的。一个可能的原因是学习率�太大。

C. 假设我们使用学习率为�的梯度下降。对于逻辑回归和线性回归，�(Θ)是一个凸优化问题，因此我们不想选择过大的学习率�。
然而，对于神经网络，�(Θ)可能不是凸的，因此选择一个非常大的�值只能加快收敛速度。

D. 如果我们使用梯度下降训练一个神经网络，一个合理的调试步骤是将�(Θ)绘制为迭代次数的函数，并确保每次迭代后它是递减的（或至少是不递增的）。

## 41-45题 答案 & 题解

41.C 42.A 43.D 44.CD 45.BD

## Week 6 | 1 机器学习的评价参数

### 第 46 题

你训练一个学习算法，发现它在测试集上的误差很高。绘制学习曲线，并获得下图。算法是否存在高偏差、高方差或两者都不存在？

![Image Name](https://cdn.kesci.com/upload/image/q3pxb7r62x.jpg?imageView2/0/w/960/h/960)

A. 高偏差
B. 高方差
C. 两者都不

### 第 47 题

假设您已经实现了正则化逻辑回归来分类图像中的对象（即，还没有实现图像识别）。然而，当你在一组新的图像上检验你的模型时，你会发现它对新图像的预测有误差非常大。然而，你的假设在训练集上拟合的很好。以下哪个做法可以改善？选出所有正确项

A. 尝试添加多项式特征
B. 获取更多训练示例
C. 尝试使用较少的特征
D. 少用训练的例子

### 第 48 题

假设您已经实现了正则化的逻辑来预测客户将在购物网站上购买哪些商品。然而，当你在一组新的客户身上测试你的模型时，你发现它在预测中的误差很大。此外，该模型在训练集上表现不佳。以下哪个做法可以改善？选出所有正确项

A. 尝试获取并使用其他特征
B. 尝试添加多项式特征
C. 尝试使用较少的特征
D. 尝试增加正则化参数�

### 第 49 题

以下哪项陈述是正确的？选出所有正确项

A. 假设您正在训练一个正则化的线性回归模型。选择正则化参数�值的推荐方法是选择交叉验证误差最小的�值。

B. 假设您正在训练一个正则化的线性回归模型。选择正则化参数�值的推荐方法是选择给出最小测试集误差的�值。

C. 假设你正在训练一个正则化线性回归模型，推荐的选择正则化参数�值的方法是选择给出最小训练集误差的�值。

D. 学习算法在训练集上的性能通常比在测试集上的性能要好。

### 第 50 题

以下哪项陈述是正确的？选出所有正确项

A. 在调试学习算法时，绘制学习曲线有助于了解是否存在高偏差或高方差问题。

B. 如果一个学习算法受到高方差的影响，增加更多的训练实例可能会改善测试误差。

C. 我们总是喜欢高方差的模型（而不是高偏差的模型），因为它们能够更好地适应训练集。

D. 如果一个学习算法有很高的偏差，仅仅增加更多的训练实例可能不会显著改善测试误差。

## 46-50题 答案 & 详解

46.A. 47.BC 48.AB 49.AD 50.ABD

## Week 6 | 3 机器学习系统设计

### 第 51 题

你正在研究一个垃圾邮件分类系统，准备使用正则化的逻辑回归。“垃圾邮件”是正类（y=1），“非垃圾邮件”是负类（y=0）。您已经训练了分类器，交叉验证集中有m=1000个示例。预测类与实际类的图表为：

```
| Actual Class: 1    | Actual Class: 0 |  
| Predicted Class: 1 | 85              |  
| Predicted Class: 0 | 15              |  
  
```

供参考：
准确度Accuracy=（真阳性+真阴性）/（总示例）
精度Precision =（真阳性）/（真阳性+假阳性）
召回Recall=（真阳性）/（真阳性+假阴性）
�1分数=（2*精确*召回）/（精确+召回）

分类器的召回是多少？

### 第 52 题

假设一个庞大的数据集可以用来训练一个学习算法。当以下两个条件成立时，对大量数据进行训练可能会产生良好的性能。两个条件是哪两个？

A. 特征x包含足够的信息来精确地预测y。（例如，一个验证这一点的方法是，当只给x时，人类专家是否能够自信地预测y）。

B. 我们训练一个具有少量参数的学习算法（因此不太可能过拟合）。

C. 我们训练具有大量参数的学习算法（能够学习/表示相当复杂的函数）。

D. 我们训练一个不使用正则化的模型。

### 第 53 题

假设您已经训练了一个输出ℎ�(�)的逻辑回归分类器。
目前，如果ℎ�(�)≥�ℎ���ℎ���，则预测1，
如果ℎ�(�)≤�ℎ���ℎ���，则预测0，当前阈值设置为0.5。

假设您将阈值增加到0.9。以下哪项是正确的？选出所有正确项

A. 现在分类器的精度可能更低。

B. 分类器的准确度和召回率可能不变，但准确度较低。

C. 分类器的准确度和召回率可能不变，但精度较高。

D. 分类器现在可能具有较低的召回率。

假设您将阈值降低到0.3。以下哪项是正确的？选出所有正确项

A. 分类器现在可能具有更高的召回率。

B. 分类器的准确度和召回率可能不变，但精度较高。

C. 分类器现在可能具有更高的精度。

D. 分类器的准确度和召回率可能不变，但准确度较低。

### 第 54 题

假设您正在使用垃圾邮件分类器，其中垃圾邮件是正例（y=1），非垃圾邮件是反例（y=0）。您有一组电子邮件训练集，其中99%的电子邮件是非垃圾邮件，另1%是垃圾邮件。以下哪项陈述是正确的？选出所有正确项

A. 一个好的分类器应该在交叉验证集上同时具有高精度precision和高召回率recall。

B. 如果您总是预测非垃圾邮件（输出y=0），那么您的分类器在训练集上的准确度accuracy将达到99%，而且它在交叉验证集上的性能可能类似。

C. 如果您总是预测非垃圾邮件（输出y=0），那么您的分类器的准确度accuracy将达到99%。

D. 如果您总是预测非垃圾邮件（输出y=0），那么您的分类器在训练集上的准确度accuracy将达到99%，但在交叉验证集上的准确率会更差，因为它过拟合训练数据。

E. 如果总是预测垃圾邮件（输出y=1），则分类器的召回率recall为0%，精度precision为99%。

F. 如果总是预测非垃圾邮件（输出y=0），则分类器的召回率recall为0%。

G. 如果您总是预测垃圾邮件（输出y=1），那么您的分类器将具有召回率recall 100%和精度precision 1%。

H. 如果您总是预测非垃圾邮件（输出y=0），那么您的分类器的准确度accuracy将达到99%。

### 第 55 题

以下哪项陈述是正确的？选出所有正确项

A. 在构建学习算法的第一个版本之前，花大量时间收集大量数据是一个好主意。

B. 在倾斜的数据集上（例如，当有更多的正面例子而不是负面例子时），准确度不是一个很好的性能度量，您应该根据准确度和召回率使用F1分数。

C. 训练完逻辑回归分类器后，必须使用0.5作为预测示例是正是负的阈值。

D. 使用一个非常大的训练集使得模型不太可能过度拟合训练数据。

E. 如果您的模型不适合训练集，那么获取更多数据可能会有帮助。

## 51-55题 答案 & 题解

51.0.85 52.AC 53.D A 54.BCD FGH 55.BD

## Week 7 | 1 支持向量机

### 第 56 题

假设您使用训练了一个高斯内核的支持向量机，它在训练集上学习了以下决策边界：

![Image Name](https://cdn.kesci.com/upload/image/q3q4r0y7l7.jpg?imageView2/0/w/960/h/960)

你觉得支持向量机欠拟合了，你应该试着增加或减少�吗？或者增加或减少�2？

A. 降低�，增加�2
B. 降低�，降低�2
C. 增加�，增加�2
D. 增加�，降低�2

### 第 57 题

高斯核的公式是由similarity(�,�(1))=exp⁡(−||�−�(1)||22�2)给出的。

下图显示了当�2=1时，�1=similarity(�,�(1))的曲线图。

![Image Name](https://cdn.kesci.com/upload/image/q3q4s14j5h.jpg?imageView2/0/w/960/h/960)

当�2=0.25时，下列哪个是�1的曲线图？

A.

![Image Name](https://cdn.kesci.com/upload/image/q3q4skngbx.jpg?imageView2/0/w/960/h/960)

B.

![Image Name](https://cdn.kesci.com/upload/image/q3q4svkneu.jpg?imageView2/0/w/960/h/960)

C.

![Image Name](https://cdn.kesci.com/upload/image/q3q4tlis0y.jpg?imageView2/0/w/960/h/960)

D.

![Image Name](https://cdn.kesci.com/upload/image/q3q4tt2le8.jpg?imageView2/0/w/960/h/960)

### 第 58 题

支持向量机求解min� �∑�=1��(�)cost1(���(�))+(1−�(�))cost0(���(�))+∑�=1���2，其中函数cost0(�)和cost1(�)图像如下：

![Image Name](https://cdn.kesci.com/upload/image/q3q4v85lz4.jpg?imageView2/0/w/960/h/960)

目标中的第一项是：�∑�=1��(�)cost1(���(�))+(1−�(�))cost0(���(�)).
如果以下四个条件中有两个为真，则第一项为零。使这个项等于零的两个条件是什么？

A. 对于�(�)=1的每个例子，有���(�)≥1

B. 对于�(�)=0的每个例子，有���(�)≤−1

C. 对于�(�)=1的每个例子，有���(�)≥0

D. 对于�(�)=0的每个例子，有���(�)≤0

### 第 59 题

假设您有一个具有n=10个特征和m=5000个示例的数据集。在用梯度下降训练逻辑回归分类器之后，您发现它与训练集欠拟合，并且在训练集或交叉验证集上没有达到所需的性能。以下哪个步骤有望改善？选出所有正确项

A. 尝试使用具有大量隐藏单元的神经网络。

B. 减少训练集中的示例数。

C. 使用不同的优化方法，因为使用梯度下降训练逻辑可能会导致局部最小。

D. 创建/添加新的多项式特征。

### 第 60 题

以下哪项陈述是正确的？选出所有正确项

A. 假设您使用支持向量机进行多类分类，并希望使用“一对所有”方法。如果你有�个不同的类，你将训练�−1个不同的支持向量机。

B. 如果数据是线性可分的，那么不管�值是多少，线性内核的支持向量机都将返回相同的参数�（即，�的结果值不依赖于�）。

C. 高斯核的最大值（即���(�,�(1))）是1。

D. 在使用高斯核之前进行特征归一化是很重要的。

## 56-60题 答案 & 题解

56.D 57.D 58.AB 59.AD 60.CD

## Week 8 | 1 无监督学习

### 第 61 题

对于以下哪些任务，K-means聚类可能是一种合适的算法？选出所有正确项

A. 给定一个关于用户信息的数据库，自动将用户分组到不同的市场细分中。

B. 根据超市中大量产品的销售数据，找出哪些产品可以组成组合（比如经常一起购买），因此应该放在同一个货架上。

C. 根据历史天气记录，预测明天的降雨量

D. 给定超市中大量产品的销售数据，估计这些产品的未来销售额。

E. 给出一组来自许多不同新闻网站的新闻文章，找出所涉及的主要主题。

F. 基于许多电子邮件，确定它们是垃圾邮件还是非垃圾邮件。

G. 从网站上的用户使用模式，找出哪些不同的用户群体存在。

H. 根据历史天气记录，预测明天的天气是晴还是雨。

### 第 62 题

假设我们有三个簇中心�1=[12],�2=[−30],�3=[42]。此外，我们还有一个训练示例�(�)=[−21]。在一个集群分配步骤之后，�(�)将是什么？

A. �(�)=2
B. �(�)未被分配
C. �(�)=1
D. �(�)=3

### 第 63 题

K-means是一种迭代算法，在其内部循环中重复执行以下两个步骤。哪两个？

A. 移动簇中心，更新簇中心��。

B. 分配簇，其中参数�(�)被更新。

C. 移动簇中心��，将其设置为等于最近的训练示例�(�)

D. 簇中心分配步骤，其中每个簇质心��被分配（通过设置�(�)）到最近的训练示例�(�)。

### 第 64 题

假设您有一个未标记的数据集{�(1),…,�(�)}。你用50个不同的随机数运行K-means初始化，并获得了50个不同的聚类。选择这50个组合中的哪一个的方法是什么？

A. 唯一的方法是我们需要数据标签�(�)。

B. 对于每一个分类，计算1�∑�=1�||�(�)−��(�)||2，并选择这个值最小的一个。

C. 答案模棱两可，没有好的选择方法。

D. 总是选择找到的最后一个（第50个）聚类，因为它更有可能收敛到一个好的解决方案。

### 第 65 题

以下哪项陈述是正确的？选出所有正确项

A. 如果我们担心K-means陷入局部最优解，一种改善（减少）这个问题的方法是尝试使用多个随机初始化。

B. 初始化K-均值的标准方法是将�1=...=��设置为等于零的向量。

C. 由于K-Means是一种无监督的学习算法，它不能对数据进行过度拟合，因此最好在计算上尽可能多的聚类。

D. 对于某些数据集，K（集群数量）的“正确”值可能是不明确的，甚至对于仔细查看数据的人类专家来说也很难做出决定。

E. 无论簇中心的初始化如何，K-均值都会给出相同的结果。

F. 初始化K-means的一个好方法是从训练集中选择K个（不同的）示例，并设置与这些选定示例相等的簇质心。

G. 在K-均值的每次迭代中，代价函数�(�(1),…,�(�),�1,…,��)（失真函数）要么保持不变，要么减小，特别是不应增加。

H. 一旦一个例子被分配到一个特定的簇中心，它将永远不会被重新分配到另一个不同的簇中心。

## 61-65题 答案 & 题解

61.AB EG 62.A 63.AB 64.B 65.AD FG

## Week 8 | 2 PCA主成分分析

### 第 66 题

考虑以下二维数据集：

![Image Name](https://cdn.kesci.com/upload/image/q3q7812zbu.jpg?imageView2/0/w/960/h/960)

下列哪个图片对应的PCA可能返回的�(1)（第一特征向量/第一主成分）的值？选出所有正确项

A.

![Image Name](https://cdn.kesci.com/upload/image/q3q7aisxr.jpg?imageView2/0/w/960/h/960)

B.

![Image Name](https://cdn.kesci.com/upload/image/q3q7arotrz.jpg?imageView2/0/w/960/h/960)

C.

![Image Name](https://cdn.kesci.com/upload/image/q3q7ayhmi8.jpg?imageView2/0/w/960/h/960)

D.

![Image Name](https://cdn.kesci.com/upload/image/q3q7b5xm86.jpg?imageView2/0/w/960/h/960)

### 第 67 题

以下哪一项是选择主成分�数量的合理方法？（n是输入数据的维度mm是输入示例的数量）

A. 选择至少保留99%的方差的k的最小值

B. 选择k，使逼近误差1�∑�=1�||�(�)−�approx(�)||2。

C. 选择至少保留1%的方差的k的最小值

D. 选择k为99%的n（即�=0.99∗�四舍五入至最接近的整数）。

### 第 68 题

假设有人告诉你，他们运行主成分分析的方式是“95%的方差被保留”，什么是与此等价的说法？

A. 1�∑�=1�||�(�)||21�∑�=1�||�(�)−�approx(�)||2≥0.05
B. 1�∑�=1�||�(�)||21�∑�=1�||�(�)−�approx(�)||2≤0.05
C. 1�∑�=1�||�(�)−�approx(�)||21�∑�=1�||�(�)||2≤0.05
D. 1�∑�=1�||�(�)||21�∑�=1�||�(�)−�approx(�)||2≤0.95

### 第 69 题

以下哪项陈述是正确的？选择所有正确项

A. 仅给出�(�)和�reduce，就没有办法重建�(�)的任何合理的近似。

B. 即使所有的输入特征都在非常相似的尺度上，在运行PCA之前，我们仍然应该执行均值归一化（这样每个特征的均值为零）。

C. PCA易受局部最优解的影响；尝试多次随机初始化可能会有所帮助。

D. 给定输入数据�∈��，仅用满足�≤�的k值运行PCA是有意义的（特别是，用k=n运行PCA是可能的，但没有帮助，�>�没有意义）

### 第 70 题

以下哪项是PCA的推荐应用？选择所有正确项

A. 作为线性回归的替代：对于大多数模型应用，PCA和线性回归给出了基本相似的结果。

B. 数据压缩：减少数据的维数，从而减少占用的内存/磁盘空间。

C. 数据可视化：获取二维数据，并在二维中找到不同的绘制方法（使用k=2）。

D. 数据压缩：减少输入数据�(�)的维数，该维数将用于监督学习算法（即，使用PCA以使监督学习算法运行更快）。

## 66-70题 答案 & 题解

66.AB 67.A 68.C 69.BD 70.BD

## Week 9 | 1 异常检测

### 第 71 题

对于下列哪一个问题，异常检测是一个合适的算法？

A. 给定一张脸的图像，确定它是否是某个特定名人的脸。

B. 给定信用卡交易的数据集，识别异常交易，将其标记为可能存在欺诈。

C. 给定信用卡交易的数据，根据购买类型对每个交易进行分类（例如：食物、交通工具、衣服）。

D. 从大量的初级保健患者记录中，找出可能有异常健康状况的个人。

### 第 72 题

假设您已经训练了一个异常检测系统，当�(�)<�时标记异常，并且您在交叉验证集中发现它有太多的误报（标记太多的东西为异常）。你该怎么办？

A. 增大�
B. 减小�

### 第 73 题

假设您正在开发一个异常检测系统来捕获飞机发动机中的制造缺陷。你的模型用�(�)=∏�=1��(��;��,��2)。
有两个特性�1=振动强度，�2=产生的热量，�1,�2的值都在0到1之间（并且严格大于0）。
对于大多数“正常”发动机，你期望�1≈�2。其中一个可疑的异常是，即使不产生太多热量，发动机也会剧烈振动（大�1，小�2），即使�1和�2的特定值可能不在其典型值范围之外。
您应该构造哪些特征�3来捕获这些类型的异常：

A. �3=�12×�2
B. �3=�1�2
C. �3=�1+�2
D. �3=�1×�2

### 第 74 题

以下哪项是正确的？选择所有正确项

A. 如果没有任何标记的数据（或者如果所有数据都有标记�=0），则仍然可以学习�(�)，但可能更难评估系统或选择一个好的值。

B. 如果你有一个带有许多正例子和许多负例子的训练集，那么异常检测算法的性能可能与有监督的学习算法（如支持向量机）一样好。

C. 如果您正在开发异常检测系统，则无法使用标记的数据来改进您的系统。

D. 在为异常检测系统选择特征时，最好为异常示例寻找具有异常大值或小值的特征。

### 第 75 题

您有一个一维数据集{�(1),…,�(�)}，并且希望检测数据集中的异常值。首先绘制数据集，它如下所示：

![Image Name](https://cdn.kesci.com/upload/image/q3q91n2w78.jpg?imageView2/0/w/960/h/960)

假设将高斯分布参数μ1μ1和σ21σ12拟合到此数据集。对于�1,�12，可以得到下列哪个值？

A. �1=−3,�12=4
B. �1=−6,�12=4
C. �1=−3,�12=2
D. �1=−6,�12=4

## 71-75题 答案 & 题解

71.BD 72.B 73.B 74.AD 75.A

## Week 9 | 2 推荐系统

### 第 76 题

假设你开了一家书店，对书的评级为（1到5星）。协作过滤算法为用户j学习了参数向量�(�)，为每本书学习了特征向量�(�)。你需要计算“训练误差”，即你的系统对你从用户那里得到的所有评分的预测的平均平方误差。以下哪种方法是正确的（选出所有正确项）？
对于这个问题，设m为您从用户那里获得的评分总数（�=∑�=1��∑�=1���(�,�)。

A. 1�∑�=1��∑�:�(�,�)=1((�(�))���(�)−�(�,�))2
B. 1�∑�=1��∑�:�(�,�)=1(∑�=1�(�(�))���(�)−�(�,�))2
C. 1�∑(�,�):�(�,�)=1∑�=1�((�(�))���(�)−�(�,�))2
D. 1�∑(�,�):�(�,�)=1(∑�=1�(�(�))���(�)−�(�,�))2

### 第 77 题

在下列哪种情况下，协同过滤系统是最合适的学习算法（与线性或逻辑回归相比）？

A. 你经营一家在线书店，收集许多用户的评价。你想用它来识别哪些书彼此“相似”（即，如果一个用户喜欢某本书，那么她可能也喜欢哪些书？）

B. 你管理一个在线书店，你有许多用户的书评。你想根据一本书的平均评分来预测预期的销售量（售出的书的数量）。

C. 你是个艺术家，为你的客户手绘肖像。每个客户都会得到不同的肖像（他们自己）并给你1-5星级的评价反馈，每个客户最多购买1幅肖像。你想预测下一个客户会给你什么样的评分。

D. 你开了一家服装店，出售许多款式和品牌的牛仔裤。你已经收集了经常购物者对不同款式和品牌的评论，你想用这些评论为那些购物者提供你认为他们最有可能购买的牛仔裤的折扣

### 第 78 题

你经营着一个电影公司，想要建立一个基于协同过滤的电影推荐系统。有三个受欢迎的评论网站（我们称之为A、B和C），用户可以去给电影打分。你刚刚收购了三家经营这些网站的公司，希望将三个公司的数据集合并在一起，以构建一个单一/统一的系统。
在A网站上，用户将一部电影分为1到5颗星。在B网站上，用户的排名是1-10分，允许使用小数（如7.5）。在C网站，收视率从1到100。您还拥有足够的信息来识别一个网站上的用户/电影和另一个网站上的用户/电影。
以下哪个陈述是正确的？

A. 您可以将三个数据集合并为一个数据集，但是您应该首先规范化每个数据集的评级（比如将每个数据集的评级重新调整为0-1范围）。

B. 只要在合并数据后执行平均规格化和特征缩放，就可以将所有三个训练集合并为一个。

C. 假设在一个数据库中至少有一个电影/用户没有出现在第二个数据库中，那么就没有合并这些数据集的合理方法，因为缺少数据。

D. 无法合并这些网站的数据。你必须建立三个独立的推荐系统。

### 第 79 题

以下哪项是协作过滤系统的正确选择？选出所有正确项

A. 基于内容的推荐算法的代价函数是�(�)=12∑�=1��∑�:�(�,�)=1((�(�))��(�)−�(�,�))2+�2∑�=1��∑�=1�(��(�))2。假设只有一个用户，他对训练集中的每一部电影都进行了分级。这意味着对于每个�,�，有��=1和�(�,�)=1。在这种情况下，成本函数�(�)等价于用于正则化线性回归的函数。

B. 利用梯度下降训练协同过滤系统时，可以将所有参数（�(�),�(�)）初始化为零。

C. 如果你有一个用户对某些产品的评级数据集，你可以使用这些数据来预测他对没有评级的产品的偏好。

D. 要使用协作过滤，您需要为数据集中的每个项目（例如，电影）手动设计一个特征向量，该向量描述该项目最重要的属性。

### 第 80 题

假设有两个矩阵�,�，其中�是5x3，�是3x5。它们的乘积是�=��，一个5x5矩阵。此外，还有一个5x5矩阵R，其中每个条目都是0或1。你想找到所有元素�(�,�)的和，对应的�(�,�)是1，忽略所有�(�,�)=0的元素�(�,�)。一种方法是使用以下代码：

![Image Name](https://cdn.kesci.com/upload/image/q3qa2x583a.jpg?imageView2/0/w/960/h/960)

下面哪一段代码也能正确计算出这个总数？选出所有正确项

A. total = sum(sum((A * B) .* R))
B. C = A * B; total = sum(sum(C(R == 1)));
C. C = (A * B) * R; total = sum(C(:));
D. total = sum(sum(A(R == 1) * B(R == 1));

## 76-80题 答案 & 题解

76.BD 77.AD 78.A 79.AC 80.AB

## Week 10 | 1 大规模机器学习

### 第 81 题

假设您正在使用随机梯度下降训练逻辑回归分类器。你发现在过去的500个例子中，成本（即����(�,(�(�),�(�)))，500个例子平均后）绘制为迭代次数的函数，随时间缓慢增加。以下哪项更改可能有帮助？

A. 试着在图中用较少的例子（比如250个例子而不是500个）来计算平均成本。

B. 这在随机梯度下降的情况下是不可能的，因为它保证收敛到最优参数�。

C. 尝试将学习率�减半（减少），看看这是否会导致成本持续下降；如果没有，继续减半直到成本会持续下降。

D. 从训练集中取更少的例子

### 第 82 题

下列关于随机梯度下降的陈述哪一个是正确的？选出所有正确项

A. 您可以使用数值梯度检查的方法来验证您的随机梯度下降实现是对的（随机梯度下降自重一步是计算偏导数∂∂������(�,(�(�),�(�)))）

B. 在运行随机梯度下降之前，您应该随机洗牌（重新排序）训练集。

C. 假设您使用随机梯度下降来训练线性回归分类器。代价函数�(�)=12�∑�=1�(ℎ�(�(�))−�(�))2一定会随着每次迭代减小。

D. 为了确保随机梯度下降收敛，我们通常在每次迭代后计算�train(�)，并绘制它，以确保成本函数总体上是递减的。

### 第 83 题

以下关于在线学习的陈述哪一个是正确的？选出所有正确项

A. 如果我们有一个连续/不间断的数据流，用在线学习算法通常是最适合的。

B. 当我们有一个大小为m的固定训练集需要训练时，在线学习算法是最合适的。

C. 使用在线学习时，您必须保存获得的每个新培训示例，因为您将需要重用过去的示例来重新训练模型，即使在将来获得新的训练例子之后也是如此。

D. 在线学习的一个优点是，如果我们正在建模的功能随着时间的推移而变化（例如，如果我们正在建模用户单击不同URL的概率，并且用户的品味/偏好随着时间的推移而变化），在线学习算法将自动适应这些变化。

### 第 84 题

假设您有一个非常大的训练集，您认为以下哪种算法可以使用map-reduce和跨不同机器拆分训练集来并行化？选出所有正确项

A. 用随机梯度下降训练逻辑回归

B. 用随机梯度下降训练线性回归

C. 用批量梯度下降训练逻辑回归

D. 计算训练集中所有特征的平均值�=1�∑�=1��(�)（例如为了执行平均归一化）。

### 第 85 题

下面关于map-reduce的哪些语句是正确的？选出所有正确项

A. 由于网络延迟和其他与map-reduce相关的开销，如果我们使用N台计算机运行map-reduce，与使用1台计算机相比，我们可能会得到小于N倍的加速。

B. 如果您只有一台具有一个计算核心的计算机，那么map-reduce不太可能有帮助。

C. 当使用带梯度下降的map-reduce时，我们通常使用一台机器从每个map-reduce机器中累积梯度，以便计算该迭代的参数更新。

D. 线性回归和逻辑回归可以用map-reduce并行化，但神经网络训练不能。

## 81-85题 答案 & 题解

81.C 82.AB 83.AD 84.CD 85.ABC

## Week 11 | 1 图片文字识别

### 第 86 题

假设您正在运行一个滑动窗口检测器来查找图像中的文本。您的输入图像为1000x1000像素。你将在两个尺寸下运行你的滑动窗口探测器，10x10和20x20（即，您将在大量10x10的窗口上运行分类器，以确定它们是否包含文本；同样的，也在20x20的窗口上），你将每次滑动你的探测器2像素。
那么，在单张1000x1000的测试图像上，运行分类器的次数是多少？

A. 500,000
B. 1,000,000
C. 100,000
D. 250,000

### 第 87 题

假设您刚刚加入了一个产品团队，该团队使用训练数据开发了一个机器学习应用程序。您发现您可以选择雇用其他人员来帮助收集和标记数据。
你估计你得给每个标记工每小时10美元，每个标记工每分钟可以标记4个样本。
雇佣标记工给10000个新的训练数据打标签要花多少钱？

A. 400�.600
C. 250�.10,000

### 第 88 题

进行上限分析有什么好处？选出所有正确项

A. 这是为算法提供额外训练数据的一种方法。

B. 使用上限分析能帮助我们分析流水线的哪个部分对整个系统的提高最大。

C. 使用上限分析能让我们知道到某个模块需不需要花精力做好;因为就算把这个模块精度提高到100%了,也无助于提高整个系统的精度。

D.使用上限分析并不会帮我们分析出哪个部分是high bias,哪个部分是high variance。

### 第 89 题

假设您正在构建一个对象分类器，它将图像作为输入，并将该图像识别为包含汽车（y=1y=1）或不包含汽车（y=0y=0）。例如，这里有正例和一个负例：

![Image Name](https://cdn.kesci.com/upload/image/q3qcbiu7e3.png?imageView2/0/w/960/h/960)

在仔细分析了算法的性能之后，你的结论是你需要更多正例（�=1）。下面哪一个可能是获得更多正面例子的好方法？

A. 对现有训练集中的图像应用平移、扭曲和旋转。

B. 选择两个汽车图像并对其进行平均以生成第三个示例。

C. 从训练集中获取一些图像，并向每个像素添加随机高斯噪声。

D. 为训练集中的每个图像制作两份副本；这会立即使训练集大小加倍。

### 第 90 题

假设您有一个图片手写字符识别系统，其中有以下流水线：

![Image Name](https://cdn.kesci.com/upload/image/q3qcggupac.jpg?imageView2/0/w/960/h/960)

您已决定对此系统执行上限分析，并得到以下内容：

![Image Name](https://cdn.kesci.com/upload/image/q3qchi50uw.png?imageView2/0/w/960/h/960)

以下哪项陈述是正确的？

A. 提高字符识别系统的性能是可能的。

B. 执行此处的上限分析，需要我们对其它的三个流程都加上标签来判断对错(ground-truth)。

C. 最没有前途的部分是字符识别系统，因为它已经获得了100%的准确率。

D. 最有前途的组件是文本检测系统，因为它的性能最低（72%），因此潜在增益最大。

## 86-90题 答案 & 题解

86.A 87.A 88.BC 89.A 90.AB