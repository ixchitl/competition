# 模型微调赛题

## 赛题介绍

### 第一阶段

本赛题要求基于开源中英文混合数学运算数据集，跑通baseline，并对MindFormers中LLama3-8b模型进行微调（LoRA或其他微调算法）。微调后的模型在原有能力不丢失的前提下（需保持在原能力的90%及以上），回答数学运算准确率相对baseline有提升，按照低参比例及准确率进行综合排名。

1. 模型原有能力以其在SQUAD数据集上的阅读理解能力为准，评价标准为F1 Score和Em Score，要求微调后两项评价指标需要给定阈值以上方可算作有效作品，如何进行原有能力评估，以及F1 Score和Em Score的参考阈值，请参考下方-原有能力评估。

2. 运算准确率评价标准：模型基于测试数据集（不公开，与训练数据集格式相同，为数道中英文数学运算题）进行推理，生成数学运算结果，如计算结果（数值）与正确答案相同，则视为本题正确，最终统计在测试数据集上回答正确的题目数量占比。

运算准确率 = 正确运算题目数 / 测试集总题目数

3. 低参比例：低参比例为微调参数量在总参数量的占比，选手在提交作品时需提供低参比例的计算结果，如何进行低参比例详见下方-低参比例运算。

低参比例 = 参与微调的参数量 / 模型总参数量

4. 低参比例和运算准确率综合排名：低参比例越低越好，准算准确率越高越好，按照如下加权进行运算。

( 100% - 低参比例 ) * 0.3 + 运算准确率 * 0.7

5. 本题目共提供80万条中英文混合题目作为训练数据集，选手可根据自己的实际情况调整数据集规模，建议综合在微调及推理时长、算力需求、维持模型原有能力、模型运算准备率提升等多方面因素进行训练数据集规模的评估。

> 参考：9万条数据集在4卡的LoRA微调下的运行时长为6个小时（seq_len为256，batch_size为64，微调5个epochs）


### 第二阶段

本赛题要求基于中英文选择题数据集，跑通baseline，并对MindFormers中InternLM-7B模型进行微调（LoRA或其他微调算法）。微调后的模型在原有能力不丢失的前提下（需保持在原能力的90%及以上），回答数学运算准确率相对baseline有提升，按照低参比例及准确率进行综合排名，评选出1个金奖2个银奖3个铜奖。

1. 模型原有能力以其在SQUAD数据集上的阅读理解能力为准，评价标准为F1 Score和Em Score，要求微调后两项评价指标需要给定阈值以上方可算作有效作品，如何进行原有能力评估，以及F1 Score和Em Score的参考阈值，请参考指导手册。

2. 单选题准确率评价标准：模型基于测试数据集（不公开，与训练数据集格式相同，为数道单选题）进行推理，生成回答结果，最终统计在测试数据集上回答正确的题目数量占比：

准确率 = 正确答案题目数 / 测试集总题目数

注：baseline的准确率为40%，请以此为参考进行微调。

3. 低参比例：低参比例为微调参数量在总参数量的占比，选手在提交作品时需提供低参比例的计算结果，如何进行低参比例详见下方-低参比例运算。

低参比例 = 参与微调的参数量/模型总参数量

4. 低参比例和运算准确率综合排名：低参比例越低越好，运算准确率越高越好，按照如下加权进行运算：
（100%-低参比例 * 10）* 0.3 + 运算准确率 * 0.7

5. 本题目共提供2.7+万条中英文混合题目作为训练数据集，选手可根据自己的实际情况调整数据集规模，建议综合在微调及推理时长、算力需求、维持模型原有能力、模型运算准备率提升等多方面因素进行训练数据集规模的评估。

6. 相关资料及要求如下：

（1）操作指导手册：待补充

（2）MindSpore资源：https://www.mindspore.cn/

（3）完成微调，选手需提交作品，包含如下所有内容：
- 微调算法介绍；
- 超参配置;
- 代码文件;
- 微调后的ckpt，需要5份，在微调过程中按照平均间隔保存5份权重（权重需为合并后的完整权重），比赛将以在测试数据集上效果最好的权重得分计为选手最终成绩。平均间隔：保存权重的时刻需均匀分布在微调过程中，假设微调了10个epoch，可以提供第2、4、6、8、10个epoch的权重；如微调了20个epoch，可以提供第4、8、12、16、20个epoch的权重，以此类推。
- 自验结果，包含运行日志、准确率、低参比例等的截图；
- 运行环境介绍（在基础环境上额外安装的依赖）。



## 获奖作品展示

第一阶段大模型微调赛题已完成，获奖团队如下所示：


| 作品名称 | 团队名称 | 数学运算准确率 | 低参比例 | 最终得分 | 排名 |  作品链接 |
| :--: | :--: | :--: | :--: | :--: | :--: |  :--: |
| debias_world1.zip | debias_world1 | 71.61% | 0.00679028 | 0.799232916 | 1 | https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/nju-websoft   |
| 枪心如火，枪如我心.zip | 枪心如火，枪如我心 | 70.59% | 0.00169757 | 0.793620729 | 2 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/枪心如火，枪如我心   | 
| 肆拾贰.zip | 肆拾贰 | 64.00% | 0.000424393 | 0.747872682 | 3 |   https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/肆拾贰 | 
| 南科启明-提交文档.zip | 南科启明 | 61.54% | 0.000424393 | 0.730652682 | 4 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/南科启明   | 
| 崩铁暴打zzz.zip | 崩铁暴打zzz | 51.38% | 0.000424393 | 0.659532682 | 5 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/崩铁暴打zzz   | 
| aics.zip | aics | 48.20% | 0.000424393 | 0.637272682 | 6 | https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/aics    | 
| 模型微调-0801.zip | PEFT小队 | 45.54% | 0.000848785 | 0.618525364 | 7 | https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/PEFT小队     |
| 慢调细磨.zip | 慢调细磨 | 41.56% | 0.000424393 | 0.590792682 | 8 | https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/慢调细磨   |  
| nju-websoft.zip | nju-websoft | 36.44% | 0.000424393 | 0.554952682 | 9 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/nju-websoft   | 
| 起名字是这样的，我考虑的就多了.zip | 起名字是这样的，我考虑的就多了 | 33.56% | 0.000424393 | 0.534792682 | 10 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/起名字是这样的，我考虑的就多了    |
| 你当我是LZMA吗.zip | 你当我是LZMA吗 | 32.05% | 	0.000424393 | 	0.524222682 | 11 | https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/你当我是LZMA吗   |
| 阿巴阿巴-模型微调.zip | 阿巴阿巴 | 30.10% | 0.000636589 | 0.510509023 | 12 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/_阿巴阿巴   | 
| dian-team.zip | dian-team | 30.04% | 0.000424393 | 0.510152682 | 13 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/dian-team  |  
| 作品提交.zip | ALL IN ONE | 29.87% | 0.000424393 | 0.508962682 | 14 |   https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/ALL%20IN%20ONE  | 
| 搞搞镇文化科技.zip | 搞搞镇文化科技 | 27.74% | 0.000212196 | 0.494116341 | 15 |   https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/搞搞镇文化科技   |
| 提交汇总.zip | 欢迎光临 | 27.55% | 0.000424393 | 0.492722682 | 16 |   https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/欢迎光临   |
| 牛牛向前冲-常科.zip | 牛牛向前冲 | 26.00% | 0.000424393 | 0.481872682 | 17 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/牛牛向前冲    |
| 阿巴巴巴.zip | 阿巴巴巴 | 25.64% | 0.000685557 | 0.479274333 | 18 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/阿巴巴巴   | 
| 九毛一斤的瓜大队.zip | 九毛一斤的瓜大队 | 23.55% | 0.000424393 | 0.464722682 | 19 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/九毛一斤的瓜大队  |
| 比奇堡冲浪小组.zip | 比奇堡冲浪小组 | 22.40% | 0.000424393 | 0.456672682 | 20 |  https://github.com/mindspore-courses/competition/tree/master/2024-ascend-innovation-contest/topic2-finetune/first-phase/比奇堡冲浪小组  |



***后续操作详见[2024昇腾AI创新大赛MindSpore赛道实验指导手册](../2024昇腾AI创新大赛MindSpore赛道实验指导手册.pdf)***
