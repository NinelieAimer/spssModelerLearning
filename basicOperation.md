# 这个笔记讲述SPSS Modeler的基本操作

## 用户界面介绍

![1551150190634](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551150190634.png)

- 节点：下面每创造一个图标就是创建一个节点，类似于git操作
  - 源节点：就是导入数据的
  - 记录选项节点：就是一条记录是指一行，这是指对行进行操作
  - 字段选项：就是对字段进行操作
  - 图形节点：用来可视化的
  - 建模节点：引入算法的
  - 输出：也像是可视化对数据进行处理感觉
  - 导出：将数据转换成其他格式的节点
- 工作流：一系列的节点连成的东西
- 选项板：就是包含一系列功能面板

## 节点操作

### 增加节点

这个就不用说了双击就好

### 链接节点，删除链接

按住alt键拉出去就可以链接，能不能链接你自己判断。中间右键就可以删除

ps:

源节点只负责输出数据，不能被连入

输出的节点就是终端节点，不能链接到任何节点

## 帮助菜单

## 读取数据文件

### 可读取的数据文件

- 文本文件
  - 一种是由分隔符的，按照分隔符分割即可
  - 一种是长度一定，可以看字符串切割的
- statistics数据文件
- ODBC兼容的数据库
- SAS数据文件
- 用户输入文件



#### 文本文件的读取

- 一种可以直接按照分隔符读取
- 一种用固定长度字符串切割读取

#### 读取Statistics的数据文件

这个很简单，打开就好，但是记得全部要选择读取名称和标签

#### 读取数据库节点前必须配置

- 使用数据库节点前必须配置ODBC驱动去制定数据库位置
- 去控制面板的管理工具里面

## 定义字段类型

### 字段类型

- 连续型
- 离散型：用于当一个具体值的精确数量未知时描述字符串，一旦数据被读取，其类型就会是标记、集合或者无类型
- 集合型：用于描述带有多个具体数值的数据（黄、绿、蓝）
- 标记型（布尔型）
- 无类型：用于不符合上述任一种类型的数据或者含有太多元素的集合类型数据

![1551152426074](C:\Users\57206\AppData\Roaming\Typora\typora-user-images\1551152426074.png)

### 字段实例化

读取前为未实例化，读取后为实例化，类型和类型都是可知的

### 方向

输入：就是输入或者预测字段

输出：输出或者被预测字段

两者：既是输入，也是输出，**只在关联中用到**

无：建模过程不使用该字段

分区：将数据拆分训练、测试（验证）部分

分割：为每个不同的值建立不同的模型

**字段方向设置只有在建模时候才会起作用**

## 数据的质量

### 数据缺失类型

- 系统缺失值，也被称作 nulls，这些值在数据库中被留为空格，而且在类型节点上它们并不被明确设置为“缺失”系统缺失值在 SPSS Modeler中显示为 $null$
- 用户自定义缺失值，也被称作空白 blanks，这些值在类型节点上被明确地定义为缺失确定为空白的数据值被标记为特殊对待，而且在大多数计算中被剔除

### 手动设置缺失值

- 选中，缺失，点击“开”
- 然后进入具体字段，定义空白下面加入数字
- 最后还要读取值

## 数据审核

数据审核就是用来找关系的，设置好参数，然后让他输出各种结果，找出对应关系就好

## 数据处理技术

- CLEM（  Clementine Language for Expression Manipulation ）是一种功能强大的语言，用来分析操作 SPSS Modeler 中使用的数据
- 用在**导出、选择、过滤、平衡**，这里是对应在字段操作中的等节点
  - 这些函数可以导出新的值、根据条件选择记录、比较和评估数据、插入数据

**注意：为了将错误减少到最小，当使用** **CLEM****时经常需要为字段名加上单引号**

### 表达式构造器

尽量不手动输入CLEM表达式，一般用在字段操作和记录里面

### 选择节点

就是用来筛选出符合某种条件的记录

### 过滤节点

这个就不多说了，可以去掉某个字段，还可以改变字段名

用户自定义缺失值：这些值就在类型节点上明确被定为空白被特殊对待，而且大多数计算

工作流：就是一个线

选项板：就是一些列不同功能

### 导出字段

就是导出字段，一般都是按照某种规则导出字段，新建字段

有四种导出方式

- 导出规则
- 导出标记
- 导出集合
- 导出条件

### 重新分类节点

- 使用重新分类节点连接最后一个导出节点、			
  - 选择单一模式
- 重新分类某个字段为新字段
  - 设置原始值和新值
- 使用制表节点输出表格
  - 通过表格比较两个字段

### 设为标记节点

- 设置为标记节点
- 设置标志节点用于根据为一个或多个集合字段定义的分类值导出标志字段

## 寻找数据之间的关系

### 在数据中寻找关系

- 数据审核节点使用目标字段层叠
- 矩阵节点生成符号数据交叉列联表
- 网络图节点可视化表现符号数据之间的关系
- 统计量节点计算数值字段之间的相关系数
- 散点图节点和直方图节点可视化表现数值数据（交叠符号字段）
- Statistics输出节点实现更加复杂的关系呈现

### 矩阵节点：关联两个符号字段（在输出里面）

- 使用矩阵节点连接类型节点生成列联表
- 注意：在输出矩阵的显示条目，用户可以直接选择何种汇总方式生成列联表

### 网络图节点：可视化表现符号字段（在图形里面）

- 线段值为绝对数值
- 连接规模连续变化
- 只显示大于300的链接
- 400以下为弱连接，600以上为强连接
- 输出网络图
- 网络图的修改
  - 使用滑动可以丢弃一些弱连接

### 统计量节点

这个是在输出里面的，专门用来统计数据量的

### 散点图节点

- 使用散点图节点连接类型节点
  - x字段，y字段，交叠
- 选项条目中：
  - 散开
  - 使用全部数据

### 直方图节点

- 使用直方图节点连接类型节点
  - 字段
  - 交叠
- 选项条目
  - 指定范围

## 复杂数据处理技术

### 使用抽样节点抽取样本

使用抽样节点抽取样本即可，设计随机值抽取百分比

### 使用导出、选择节点抽取样本
