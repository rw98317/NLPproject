# NLPproject
语言信息处理大作业数据集相关
# 环境
Python 3.6 + PyTorch 0.4 
# 数据集
COCO 2014 dataset .[下载].(http://cocodataset.org/#download) 。需要下载其中的train2014.zip、val2014.zip。(另外如果想跑自行准备字幕数据的话还需要下载annotations_trainval2014.zip)<br/>
然后下载Karpathy对COCO 2014数据集的train/val/test的重分割。.[下载].(http://cs.stanford.edu/people/karpathy/deepimagesent/caption_datasets.zip) <br/>

如果想在coco上评估，需要下载COCOAPI.[下载].(https://github.com/cocodataset/cocoapi)【注：使用其中的PythonAPI，并且确保安装了Cpython】和COCO caption toolkit.[下载].(https://github.com/tylin/coco-caption)并将其重命名为`cococaptioncider`。【注：不要忘了下java】

还需要使用到bottom up features，下载数据集.[下载].(https://imagecaption.blob.core.windows.net/imagecaption/trainval_36.zip)。使用.[这里].(https://github.com/hengyuan-hu/bottom-up-attention-vqa)的方法进行处理。提取到的train36.hdf5和val36.hdf5放在文件夹`bottom-up features`下。

处理好的字幕文件.[下载].(https://drive.google.com/open?id=1vuE0Tj1a1wH-Yh2G_i6Mh1lHiIMM9b7V),其中文件均用作训练使用。
