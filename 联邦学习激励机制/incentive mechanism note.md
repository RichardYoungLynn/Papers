需了解的名词： individually rational（reward-cost>=0，也就是保证client不亏），如何证明这是一个NP问题（Multiple Knapsack Problem with Assignment Restrictions (MKAR)、Multiple Knapsack Problem (MKP) ），nonconvex问题，crowdsensing和crowdsourcing

idea：惩罚机制，惩罚那些不愿意参与的client，如果最开始不参加，那么之后相同的任务也别参加，但最终目标是提高性能。b站诺贝尔经济学获奖者的拍卖方法应用到激励机制里。软件工程的方法。

incentive mechanism design driven by client data contribution：data quantity（攻击：注入大量有害数据；防御：算梯度不看数据数量）

攻击方法：增加坏数据导致有毒梯度或上传有毒模型；使用较少的数据训练模型以减少时间



driven by client's contribution

​	data quality

​		shapley value

​		dynamically adjust(A Sustainable Incentive Scheme for Federated Learning)

​	data quantity(A learning-based incentive mechanism for federated learning)



driven by clients' reputation(based on block chain)



driven by clients' resource allocation

​	computational resource

​		Stackelberg game(Motivating workers in federated learning: A stackelberg game perspective, An incentive mechanism design for effificient edge learning by deep reinforcement learning)

​	communication resource

​		auction(An incentive mechanism for federated learning in wireless cellular network: An auction approach)

​		Stackelberg game(A crowdsourcing framework for on-device federated learning)



# CCF-A

## INFOCOM

### An Incentive Mechanism for Cross-Silo Federated Learning A Public Goods Perspective

#### 关键词

cross-silo（特性：server并不own全局模型，所以没必要向organization提供payment；public goods）

public goods（即计算和通信资源，个体不能被排除使用它们，而且这些资源也非必须竞争才能获得，例如无线信号，在FL可以指即使一个organization不参与训练，也可以享受训练好的全局模型）

social welfare maximization（每个organization对于模型训练所分配的processing capacity不同，valuation on the precision和cost也不同，所以必须优化processing capacity的选择，以确保organization之间有效的合作，即social welfare maximization）

reverse auction

#### 理论证明

social effificiency, individual rationality and budget balance

对于未来的工作，有一个方向是进一步考虑非独立和同分布的(non-i.i.d.)organization的数据。另一个研究方向是考虑organization可以根据其对精度和计算和通信成本的评估来选择他们参与的训练轮数的情况。

client向server发送message profiles，server去进行简单的计算以满足定义的一些限制条件。

攻击方法：message profiles可以造假



### FAIR Quality-Aware Federated Learning with Precise User Incentive and Model Aggregation

#### 关键词

learning quality estimation（利用历史学习记录来估计client的学习质量，考虑了记录的freshness，并使用指数遗忘函数来进行权重分配）

reverse auction（在给定的预算内，尽可能的招募更多的高学习质量的client）

model aggregation（设计了一种聚合算法，将模型质量集成到聚合中，并过滤掉不理想的模型更新，以进一步优化全局模型）

#### 理论证明

truthful, individually rational and computationally effificient

在未来的工作中，我们将进一步将通信和计算性能集成到FAIR中，以提高其在实际系统中的鲁棒性。

反向拍卖，client出价，也就是上报自己的cost，server给clientpayment（reward）以起到激励效果。具体过程不难，框架看起来比较有效，攻击方法尚待考虑。其中关于truthful需要再看看。



### FedServing A Federated Prediction Serving Framework Based on Incentive Mechanism

#### 关键词

bayesian game theory（使用bayesian game theory来建模provider的honest和strategic行为，并确保Bayesian Nash Equilibrium的存在，其中所有provider都将为给定的prediction queries提供真实而不是毫无意义的预测）

truth discovery algorithm（使用TD算法从honest但可能inaccurate的预测中学习高度准确的预测，以消除inaccurate预测的影响）

prediction serving（根据provider预测的真实性按比例分配公平的奖励）

block chain

incentive mechanism for worker：reverse auction，double reverse auction and all-pay auction or other game theory，大部分关注于使worker真实的反应他们的cost，少部分关注于the truthfulness of crowd data。



## WWW

### Incentive Mechanism for Horizontal Federated Learning Based on Reputation and Reverse Auction

#### 关键词

reputation（间接反映client的reliability和data quality）

reverse auction

horizontal federated learning

block chain

one-dimensional reverse GFP and GSP auctions（auction的过程中只考虑bid price）

multi-dimensional reverse auction（考虑bid price和quality）

quality detection（基于marginal contribution）

#### 理论证明

computational efficiency, individual rationality, budget feasibility and truthfulness（只有在bid的时候显露自己真实的cost，candidate才能最大化他的utility，也就是说不管其他candidate提交了什么，没人可以通过提交fake cost来提高自己的utility）

在未来，我们可以进一步研究如何更合理地衡量参与者的贡献，以及在参与者动态加入或离开任务时如何分配奖励。



## IEEE INTERNET OF THINGS JOURNAL

### A Learning-Based Incentive Mechanism for Federated Learning

#### 关键词

deep reinforcement learning

Stackelberg game

participant decision（例如用于模型训练的数据的数量）



### Hierarchical Incentive Mechanism Design for Federated Machine Learning in Mobile Networks

#### 关键词

hierarchical incentive mechanism

contract theory（在model owner和worker之间使用，旨在incentivize worker来提供高质量和数量的数据）

coalitional game（在third-party server和model owner之间使用，基于model owner的marginal contribution）

model owner（负责发放sensing task给感兴趣的worker，然后利用worker收集到的数据训练模型，模型参数可以在model owner之间交换，也可以上传至third-party server进行aggregate）

Stackelberg game



### Incentive Mechanism for Reliable Federated Learning: A Joint Optimization Approach to Combining Reputation and Contract Theory

#### 关键词

reputation（用于度量worker的reliability，进而选择高质量的worker）

block chain（reputation management）

contract theory（激励worker参与训练和共享资源，例如数据、计算和通信资源，每个worker选择一个合适的contract item来最大化他的收益）



## VLDB

### Refiner: A Reliable Incentive-Driven Federated Learning System Powered by Blockchain

#### 关键词

block chain

incentivize self-interested participants（根据participant的训练数据和local update表现，给予一定的reward，即数字加密货币）

handle malicious participants（采用audit scheme，从participants中选择一些validator，利用smart contract跟踪训练过程，惩罚背离学习协议的participant，不给予其reward）



## IJCAI

### A Multi-player Game for Studying Federated Learning Incentive Schemes

#### 关键词



# CCF-B

## ICDCS

### FMore: An Incentive Scheme of Multi-dimensional Auction for Federated Learning in MEC

#### 关键词

multi-dimensional auction



## TWC

### A Crowdsourcing Framework for On-Device Federated Learning

#### 关键词

Stackelberg game



### An Incentive Mechanism for Federated Learning in Wireless Cellular Networks: An Auction Approach

#### 关键词

auction



# CCF-C

## BigData

### Mechanism Design for An Incentive-aware Blockchain-enabled Federated Learning Platform

#### 关键词

block chain



## WCNC

### Auction based Incentive Design for Effificient Federated Learning in Cellular Wireless Networks

#### 关键词

auction
