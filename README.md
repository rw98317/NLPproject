# NLPproject
## 论文:BMVC2019 Look and Modify: Modification Networks for Image Captioning

# 环境
Python 3.6 + PyTorch 0.4 

# 数据集
## 输入(准备数据阶段)：
图像文件：train2014/，val2014/。</br>
注解文件：instance_train2014.json,instance_val2014.json.(80种物体类别，20种语义类别)
采用实例标注形式：
annotation{
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
重划分文件：dataset_coco.json(将coco中的train和val合并并重新划分成train/val/test)

## 输出：
captions.json (训练标注)
caplens.json  (训练字幕长度)
name.json     (coco image names whit IDs)
images.hdf5
wordmap.json
