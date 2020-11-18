# NLPproject
## 论文:BMVC2019 Look and Modify: Modification Networks for Image Captioning

# 环境
Python 3.6 + PyTorch 0.4 

# 数据集
# 使用bottom-to-up features
## 输入(准备数据)：
MS COCO2014 dataset 
图片文件：train2014/，val2014/. 放置在`data preperation/images`下 </br>
注解文件：instance_train2014.json,instance_val2014.json(正确的字幕).放置在`data preperation/caption data`下，内容：</br>
```
#其中还包含80种物体类别，20种语义类别(未列出)
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
```
重划分文件：`dataset_coco.json`(将coco中的train和val合并并重新划分成train/val/test),放置在`data preperation/caption data`下</br>

## 输出：</br>
使用`prepare_captions.py`处理以上文件，得到：
`(VAL,TEST)TRAIN_name_coco.json`  (存储图像名,例如：`COCO_train2014_000000205672.jpg`) </br>
`(VAL,TEST)TRAIN_IMAGE_coco.hdf5` (存储图像数据) </br>
`(VAL,TEST)TRAIN_CAPTIONS_coco.json` (存储encoded captions,例如：`[9488,6,50,....,0]`) </br>
`(VAL,TEST)TRAIN_CAPLENS_coco.json` (存储encoded caption length,例如:`[9488,5,50,....0]`中不为0的个数是13个，则文件中对应位置就是13) </br>
`WORDMAP_coco.json` (单词字典,存储每个单词的索引，例如：`"i": 1, "n": 2, "f": 3,...."swaddled": 9485, "dentist": 9486, "`) </br>
作为后续的`train_eval.py`的输入。</br>

## 输入(训练数据)：</br>
`(VAL)TRAIN_name_coco.json` </br>
`(VAL)TRAIN_IMAGE_coco.hdf5` </br>
`TRAIN_CAPTIONS_coco.json` </br>
`TRAIN_CAPLENS_coco.json` </br>
`WORDMAP_coco.json` </br>
`(VAL)TRAIN_CAPUTIL_coco.json` (github中直接给的，其中主要内容是previous caption，即需要修改的字幕) </br>
给的文件里面还有一个叫`(VAL,TEST)TRAIN_GENOME_DETS.json`的东西，暂时不知道是用来做什么的 </br>
## 输出：</br>
还没得到...，因为代码中有点错误，而且没改好，跑出结果的话应该就能知道数据了。</br>

# 小总结
需要修改的字幕：`TRAIN_CAPUTIL_coco.json` 
标准的字幕：原始存在`dataset_coco.json`,经过处理转变成encoded形式存在`TRAIN_CAPTION_coco.json`中
【注：我拿`TRAIN_CAPUTIL_coco.json`和`dataset_coco.json`中的字幕内容和图片做了下对比，给人感觉都是对的.....】




