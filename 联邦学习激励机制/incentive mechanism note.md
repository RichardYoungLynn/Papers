需了解的名词： individually rational（reward-cost>=0，也就是保证client不亏），如何证明这是一个NP问题（Multiple Knapsack Problem with Assignment Restrictions (MKAR)、Multiple Knapsack Problem (MKP) ），nonconvex问题，crowdsensing和crowdsourcing

idea：惩罚机制，惩罚那些不愿意参与的client，如果最开始不参加，那么之后相同的任务也别参加，但最终目标是提高性能。b站诺贝尔经济学获奖者的拍卖方法应用到激励机制里。软件工程的方法。



## INFOCOM

#### An Incentive Mechanism for Cross-Silo Federated Learning A Public Goods Perspective

关键词：

cross-silo（特性：server并不own全局模型，所以没必要向organization提供payment；public goods）

public goods（即计算和通信资源，个体不能被排除使用它们，而且这些资源也非必须竞争才能获得，例如无线信号，在FL可以指即使一个organization不参与训练，也可以享受训练好的全局模型）

social welfare maximization（每个organization对于模型训练所分配的processing capacity不同，valuation on the precision和cost也不同，所以必须优化processing capacity的选择，以确保organization之间有效的合作，即social welfare maximization）

reverse auction

理论证明：

social effificiency, individual rationality and budget balance

对于未来的工作，有一个方向是进一步考虑非独立和同分布的(non-i.i.d.)organization的数据。另一个研究方向是考虑organization可以根据其对精度和计算和通信成本的评估来选择他们参与的训练轮数的情况。

client向server发送message profiles，server去进行简单的计算以满足定义的一些限制条件。

攻击方法：message profiles可以造假



#### FAIR Quality-Aware Federated Learning with Precise User Incentive and Model Aggregation

关键词：

learning quality estimation（利用历史学习记录来估计client的学习质量，考虑了记录的freshness，并使用指数遗忘函数来进行权重分配）

reverse auction（在给定的预算内，尽可能的招募更多的高学习质量的client）

model aggregation（设计了一种聚合算法，将模型质量集成到聚合中，并过滤掉不理想的模型更新，以进一步优化全局模型）

理论证明：

truthful, individually rational and computationally effificient

在未来的工作中，我们将进一步将通信和计算性能集成到FAIR中，以提高其在实际系统中的鲁棒性。

反向拍卖，client出价，也就是上报自己的cost，server给clientpayment（reward）以起到激励效果。具体过程不难，框架看起来比较有效，攻击方法尚待考虑。其中关于truthful需要再看看。





#### FedServing A Federated Prediction Serving Framework Based on Incentive Mechanism

关键词：

bayesian game theory（使用bayesian game theory来建模provider的honest和strategic行为，并确保Bayesian Nash Equilibrium的存在，其中所有provider都将为给定的prediction queries提供真实而不是毫无意义的预测）

truth discovery algorithm（使用TD算法从honest但可能inaccurate的预测中学习高度准确的预测，以消除inaccurate预测的影响）

prediction serving（根据provider预测的真实性按比例分配公平的奖励）

block chain

incentive mechanism for worker：reverse auction，double reverse auction and all-pay auction or other game theory，大部分关注于使worker真实的反应他们的cost，少部分关注于the truthfulness of crowd data。









incentive mechanism design driven by client data contribution：data quantity（攻击：注入大量有害数据；防御：算梯度不看数据数量）

攻击方法：增加坏数据导致有毒梯度或上传有毒模型；使用较少的数据训练模型以减少时间
