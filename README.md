# OR_Learn  运筹学知识总结，以及经典模型代码的编写（python）
## 线性回归
在用代码实现线性回归模型之前，最重要的是模型的确定与建立，之后直接调用linprog()函数即可，需要注意的是：matlab中线性模型的标准形式为<br>
![](https://github.com/yangxcc/OR_Learn/raw/master/image/standard.png) <br>
因此在使用linprog()时，要注意把非标准化的数学形式转化成标准形式。<br>
灵敏度分析研究的是模型参数的取值变化对最优解或者最优基的影响，模型参数的变化包括三个部分：<br>
(1)目标函数系数的变化<br>
(2)约束条件右端值的变化<br>
(3)目标函数中价值系数的变化<br>
每种不同的变化都对应不同的解题方法。<br>
**运输问题**通常有m个产地，n个销地，其中还存在产销平衡，产销不平衡两种形式，运输问题显然是一个线性规划问题，但是其约束条件的系数矩阵相当特殊，
可以使用更为简单的计算方法，通常称为表上作业法，通过最小元素法（或者最大差额法，或者西北角法）求得初始基本解，通过位势法（或者闭回路）检验是否为
最优基。<br>
**整数规划**是在基本线性回归模型的基础上，添加决策变量均为整数的约束条件，求解方法有`分支定界法`和`割平面法`，两种方法最开始都是先不考虑整数条件，求出最优解，然后根据最优解来进行下一步，分支定界法是根据最优解中某一非整决策变量进行调整，找出小于其的最大整数和大于其的最小整数，经过不断的分支筛选，找出其中最优解为整数且最优值最大的一组数据。割平面法也是根据最开始求出的最优解进行下面的操作，其中最主要的操作就是将每行的系数（包括决策变量前的系数和约束条件右端的值）分解为整数部分和非负真分数部分，然后将整数部分移到一边，非整数部分移到一边，进行之后的操作，具体见文档。
