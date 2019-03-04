# drug case notes

- # 数据审核

  - 对性别进行深入分析，没有性别偏好
  - 对血压没有偏好
  - 对Na和K看不出什么东西
  - 药品x,y进行分析，发现x,y的用量很大，x,y或许对这个影响很大。尤其是Y的使用量

- # 分析相关性

  - ### 对年龄分析

  - 输出直方图，然后交叠字段设置为药品

  - ![1551682215860](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551682215860.png)

    - 所有年龄里面x,y药品基本适合所有年龄
    - B药品一般适合50岁以上
    - A药品一般在50岁一下
    - 说明年龄与效果是有相关性的

  - 用箱图看年龄和药物分布，发现B药品适合年龄较大

  - ![1551682245621](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551682245621.png)

  - 用均值输出看出来年龄和药品

![1551682268232](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551682268232.png)

重要性就是分析相关性，说明重相关

### 对性别进行分析

- 利用图形分布（这个一般是用来做分类的）
- 利用网络图形进行分析，主要是用来看相关性。
- 矩阵分析，可以用来检测相关性，原假设是不相关，而概率高达到71.1%，原假设成立
- ![1551683419053](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551683419053.png)

## 建模

使用模型，如果用了类型就直接，如果没用就会出现问题，自己要定义

这里使用之后

![1551683833426](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551683833426.png)

可以看到性别相关性较低，这里直接去掉

然后图形中的C5.0

![1551684016559](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551684016559.png)

使用全部展开，这里类似于if else语句，如果K小于0.055，k>0.037,Na小于0.68血压高就用drugA

对模型进行输出分析

![1551684147854](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551684147854.png)

这里可以看到正确率96.5%，错误3.5%。是指机器学习时候，学习这些案例正确率和错误率。**这个不能表示之后预测的准确率**。考虑用分区检测模型

也可以输出到表，最后有概率预测

## 再分析

Na和K多重散点分析

![1551684747752](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551684747752.png)

![1551684762504](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551684762504.png)

导出字段节点Na/K

![1551684813446](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551684813446.png)

利用直方图，分析Na和K的比例

![1551684954111](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551684954111.png)

发现Na和K的比例，建模分析，用C5.0的分析，**记得先加一个类型节点**，有明显相关

![1551685545538](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551685545538.png)