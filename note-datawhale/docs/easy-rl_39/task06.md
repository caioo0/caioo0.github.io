# task06:DDPG算法

> （本学习笔记来源于DataWhale-第39期组队学习：[强化学习](https://linklearner.com/datawhale-homepage/#/learn/detail/91)） ,
> [B站视频讲解](https://www.bilibili.com/video/BV1HZ4y1v7eX) 观看地址



## DDPG算法基本概念

---

### 什么是DDPG算法？

深度确定性策略梯度（Deep Deterministic Policy Gradient, DDPG）虽名为“策略梯度”，实际上是Actor-Critic的一种经典算法。除了用于动作选择的策略网络，它还大量借鉴了DQN的思想并构建价值网络来间接引导策略网络的更新。
在这里我们可以将DDPG分为两部分，一是作为“演员”（Actor）的策略网络，二是作为“评论家”的价值网络。策略网络利用策略梯度方法进行更新，但它不是直接与环境交互来计算目标函数，而是通过价值网络估计的Q值来调整自己的网络参数**θ**θ。也就是说“演员”并不直接与提供奖励的观众（环境）接触，而是利用价值网络间接地获得对动作的评价。与此同时，价值网络部分可以看作经典的DQN模型，它一方面与环境交互，利用reward来更新自己Q网络的参数**w**w；另一方面它作为评委需要估算当前状态和动作的Q值来引导策略网络的更新。由于借鉴了DQN中的一些思想，DDPG中的策略网络和价值网络也都各分为两部分，即一个用于每步更新的当前网络和一个用于计算预测的Q值及动作的目标（target）网络，后者每隔一段时间从当前网络中复制参数，加起来总共四个网络。这样可以尽量保证预测时可以得到比较稳定的Q值，有助于模型的收敛。

### DDPG算法有什么特点？

深度确定性策略梯度，顾名思义，首先是利用了神经网络来逼近Q函数，其次它是一个确定性策略，也就是对于任意状态，输出当前最佳的动作，这里是一个确定的动作，而不是一个包含概率分布的动作集。最后它是引入了策略梯度的方法来执行动作选择。

### 如何实现确定性策略？

策略网络中输出位置我们可以添加一层以tanh为激活函数的节点，它实现对于动作空间的压缩，输入一个浮点数，它都会生成[-1,1]之间的值。然后根据动作空间的实际要求，将输出值随比例扩大即可。这样同时解决了实现执行动作连续性与和确定性的问题。
