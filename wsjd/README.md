# CAIL2022——文书校对

该项目为 **CAIL2022—文书校对** 的代码和模型提交说明。

## 选手交流群

QQ群：237633234

## 任务介绍

法律文书作为司法机关及公民行使法律权利同时享受法律效益的载体，对文字内容的准确性要求及其严格。为了保障文书内容的规范性与准确性，传统的做法会采用人工查看的方式对法律文书内容进行校验。随着法律知识的不断普及，公民的法律意识明显增强，各种类型的法律文书呈现快速增长趋势，海量文书信息与有限的人力校验之间的矛盾日益凸显。

文书校对作为CAIL2022新发布的一项子任务,旨在通过机器智能文本校对技术辅助司法人员对法律文书中存在的错误进行自动检出纠正，大幅减轻人工校对工作量，同时提升提高法律文书内容准确性。本次比赛是首次基于中文司法领域数据的句子级文本校对比赛，包含了对法律文书中存在的拼写、冗余、缺失、乱序四种类型错误的自动检出及纠正。

## 数据说明

本次技术评测使用的数据集由科大讯飞提供，数据主要来源于裁判文书网公开的裁判文书和12309中国检查网公开的检察文书。数据集由包含拼写、冗余、缺失、乱序四种类型错误的法律文书句子及对应错误的人工标注两部分组成。这些包含错误的法律文书句子，一部分为法律文书中真实存在以上四种类型错误的句子，另一部分为代码自动构造生成的含有以上四种类型错误的句子并经人工筛选后得到。其中训练集规模约3000句，验证集和测试集分别约1500句，第一阶段为小规模训练集和测试集，第二阶段为全量训练集和验证集，第三阶段的全量测试集用于封测。

## 提交的文件格式及组织形式

你可以在 ``model`` 中找到最简单的提交代码的格式。你需要将你所有的代码压缩为一个 ``zip`` 文件进行提交，该 ``zip`` 文件内部形式可以参看 ``model/submit_sample.zip``。该 ``zip`` 文件**内部顶层**必须包含``main.py``，为运行的入口程序，我们会在该目录下使用``python3 main.py``来运行你的程序。

## 代码的内容

对于你的代码，你需要从``../data/data.json``中读取数据进行预测，该数据格式与下发数据格式完全一致，隐去答案信息。选手需要将预测的结果输出到``../result/result.json``中，预测结果文件为一个json格式的文件，具体可以查看 ``evaluate/result.json``。

你可以利用 ``model`` 下的文件进行进一步参考。**请注意**，在加载模型的时候请尽量使用相对路径，我们会将提交的压缩包解压到``/model``路径下然后运行。

我们提供基于[RoBERTa-wwm-ext-large, Chinese](https://github.com/ymcui/Chinese-BERT-wwm)的基线模型（训练代码），放置在``baseline``目录下，供选手参考。

## 评测脚本

评价采用F1值评价指标，综合考虑模型检出错误和纠正错误的能力，最终评价指标计算公式为：

 $综合F1值=0.8*检出错误F1+0.2*纠正错误F1$

我们在 ``evaluate`` 文件夹中提供了评分的代码，以供参考。

## 现有的系统环境

[torch1.4+transformers3.4](./envs/torch1.4+transformers3.4.txt)

[torch1.8+transformers4.9](./envs/torch1.8+transformers4.9.txt)

如果你有需要的环境，请联系比赛管理员进行安装。

## 关注我们
欢迎关注哈工大讯飞联合实验室官方微信公众号，了解最新的技术动态。

<div align=center><img width="400" height="400" src="./images/HFL.jpg"/></div>

## 问题反馈
如有问题，请在GitHub Issue中提交