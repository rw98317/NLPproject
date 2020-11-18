# NLPproject
## 论文:BMVC2019 Look and Modify: Modification Networks for Image Captioning

# 环境
Python 3.6 + PyTorch 0.4 

# 数据集
## 输入(准备数据)：
MS COCO2014 dataset 
图片文件：`train2014.zip`，`val2014.zip`. 解压放置在`data preperation/images`下 </br>
注解文件：`instance_train2014.json`,`instance_val2014.json`(注释文件).放置在`data preperation/caption data`下，格式如下：</br>
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
重划分文件：`dataset_coco.json`(正确的字幕，并将coco中的train和val合并并重新划分成train/val/test),放置在`data preperation/caption data`下</br>

## 输出：</br>
使用`prepare_captions.py`处理以上文件，得到：
`TRAIN_name_coco.json`  (存储图像名,例如：`COCO_train2014_000000205672.jpg`，按顺序对应于`TRAIN_CAPTIONS_coco.json`的字幕) </br>
`TRAIN_IMAGE_coco.hdf5` (存储图像数据) </br>
`TRAIN_CAPTIONS_coco.json` (存储已编码字幕,例如：`[9488,6,50,..,9489..,0]`，其中'9488代表一句话开始，9489代表一句话结束'，数字索引对应单词可从`WORDMAP_coco.json`找到) </br>
`TRAIN_CAPLENS_coco.json` (存储已编码字幕长度,例如:上一行的`[9488,6,50,..,9489..,0]`中不为0的个数是13个，则文件中对应位置就是13) </br>
`WORDMAP_coco.json` (单词字典,存储每个单词以及其索引，例如：`"i": 1, "n": 2, "f": 3,...."swaddled": 9485, "dentist": 9486, "`) </br>
作为后续的`train_eval.py`的输入。</br>

## 输入(训练数据)：</br>
`TRAIN_name_coco.json` </br>
`TRAIN_IMAGE_coco.hdf5` </br>
`TRAIN_CAPTIONS_coco.json` </br>
`TRAIN_CAPLENS_coco.json` </br>
`WORDMAP_coco.json` </br>
`TRAIN_CAPUTIL_coco.json` (github中直接给的，其中主要内容是previous caption，即需要修改的字幕，格式如下：`{"COCO image name": {"caption": "previous caption to modify", "embedding": [512-d DAN embedding of previous caption], "attributes": [the indiced of the 5 extracted attributes], "image_ids": the COCO image id}`) </br>
给的文件里面还有一个叫`TRAIN_GENOME_DETS.json`的东西，暂时不知道是用来做什么的，应该是bottom-to-up features中专用的 </br>
## 输出：</br>
还没得到...，因为代码中有点错误，而且没改好，跑出结果的话应该就能知道数据了。</br>

# 小总结
需要修改的字幕：`TRAIN_CAPUTIL_coco.json` </br>
标准的字幕：原始存在`dataset_coco.json`,经过处理转变成encoded形式，存在`TRAIN_CAPTION_coco.json`中 </br>
【注：我拿`TRAIN_CAPUTIL_coco.json`和`dataset_coco.json`中的字幕内容和图片做了下对比，其中有些句子(previous caption)对比标准句子是有明显错误的,需要修改;有些看起来说的没错，但是可以补充更多细节(这也是edit的一种)。】 </br>

代码和提到的一些json文件(里面无`train2014.zip`和`val2014.zip`):https://pan.baidu.com/s/1POxjymJrd9gcvjYYHTjrMQ <br>
提取码：2k3j




