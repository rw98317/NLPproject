# NLPproject
## 论文:BMVC2019 Look and Modify: Modification Networks for Image Captioning

# 环境
Python 3.6 + PyTorch 0.4 

# 数据集
# 使用bottom-to-up features
## 输入(准备数据阶段)：
图像文件：train2014/，val2014/</br>
注解文件：instance_train2014.json,instance_val2014.json.(80种物体类别，20种语义类别)</br>
采用实例标注形式：</br>
```annotation{
    "id" : int,
    "image_id" : int,
    "category_id" : int,
    "segmentation" : RLE or [polygon],
    "area" : float, 
    "bbox" : [x,y,width,height],
    "iscrowd" : 0 or 1,
}

categories[{
    "id" : int,
    "name" : str,
    "supercategory" : str,
}]
```
重划分文件：dataset_coco.json(将coco中的train和val合并并重新划分成train/val/test)</br>
字幕文件：
<train>captions.json </br>
<train>caplens.json </br>
caputil.json </br>
genome_dets.json </br>
image_names.json </br>
wordmap.json </br>



## 输出：</br>

