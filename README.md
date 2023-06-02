# X-ray-security-inspection
2022科大讯飞安检挑战赛3.0
基于mmdetection3.0，使用coco格式
科大讯飞提供了X光安检图片及其标注，共包含4416张有标注图像可用于训练和1003张无标注图像可用于测试。
首先科大讯飞的数据放置在3个文件夹下，划分训练集和验证集不太方便，将其修改名称后放入同一个文件夹。
1 使用rename.py划分数据集

2 使用voc2coco.py将VOC格式的数据转化为coco格式

3 按照mmdetection教程配置相关文件的参数以及路径，主要包括config下的模型参数文件、dataset文件、schedule文件以及 mmdet文件夹下的dataset文件

4 配置完成后使用tools下的train.py进行训练

5 使用test.py进行预测，配置训练的参数文件。如果想保存json格式的结果，需要在此之前生成一个包含test图像信息的json。

6 使用img2json，该文件将根据test图像的txt和test图像存储路径生成一份json文件，仅包含图像的基本信息无需标注。

7 修改coco_detection.py中的test_dataloader, test_evaluator(打开注释，并修改路径，指向test的json和数据)

8 保存后的json是图像-目标顺序保存的，需要转换成科大讯飞指定的json格式提交，使用mmdet2xf.py进行转换
