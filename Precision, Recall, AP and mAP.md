# Precision, Recall, AP and mAP

### 1. Confusion Matrix - 混淆矩阵

在二分类任务中，输入样本会被分配为两种类型，1和0，或者positive和negative，混淆矩阵用来衡量模型在分类时是否“混淆”：

<img src="C:\Users\19726\Desktop\confusion matrix.png" alt="confusion matrix" style="zoom: 50%;" />

行表示样本实际的labels，列表示样本预测的labels，每个单元（红、绿）包含了两个单词：

1. True（预测准确） or False（预测错误）

2. Positive or negative（样本真实labels）

**True Positive: **真阳，将positive正确预测为positive的次数；

**False Positive: **假阳，将positive错误预测为negative的次数；

**True negative: **真阴，将negative正确预测为negative的次数；

**False negative: **假阴，将negative错误预测为positive的次数。

对于多分类任务，只需每次将一类设置为positive，其余为negative，迭代进行计算即可。

### 1. Accuracy

准确率，衡量样本中被准确预测的比率。当样本类别严重分配不均时，该评价指标不适用。
<img src="https://latex.codecogs.com/svg.image?Accuracy&space;=&space;\frac{True&space;\small&space;(positive)&space;&plus;&space;True&space;\small&space;(negative)}{True\small&space;(positive)&space;&plus;&space;True\small&space;(negative)&space;&plus;&space;False\small&space;(positive)&space;&plus;&space;False\small&space;(negative)}" title="Accuracy = \frac{True \small (positive) + True \small (negative)}{True\small (positive) + True\small (negative) + False\small (positive) + False\small (negative)}" />

### 2. Precision

精确率，查准率，表示在所有预测为positive（真实labels包含positive和negative）的样本中，正确预测的比率。
$$
Precision = \frac{True \small (positive)}{True\small (positive) + False\small (positive)}
$$
当模型将真正的positive预测错误，模型本身只有很少部分是positive（会增加将negative错误预测成positive的风险，False positive），Precision值较小；

当模型正确预测出很多positive（True Positive），或者尽量不把negative预测成positive时（False negative），precision值较大。

precision意义在于当模型预测出positive时的可信程度。目标在于将所有positive都正确预测，并且不把negative错误预测成positive。

### 3. Recall

查全率，召回率，表示正确预测的positive的个数占所有positive个数的比率，衡量模型检测出positive样本的能力，当recall值越大，模型检测出positive的个数越多。
$$
Recall = \frac{True \small (positive)}{True\small (positive) + False\small (negative)}
$$
recall只关心positive样本的分类结果，与negative样本的分类结果无关，因此，计算recall时，negative样本的分类结果可以完全忽略。

### 4. Precision-Recall Curve

**High Precision Low Recall: **模型预测对于positive的预测比较准确，但是并没有很好的把所有positive样本都预测出来；

**Low Precision High Recall:** 模型将大多数positive都正确预测出来了，但是也容易将个别negative错误预测成positive。

因此，对于不同的**threshold**，会产生PR曲线，用来得出最佳的threshold，使得P和R都相对较大。









