# Attention over Attention
这是我仿照github上面一个用户的代码，仅对其中少量部分代码进行了修改，是代码支持tf1.0及以上版本<br>
源代码链接为：https://github.com/OlavHN/attention-over-attention <br>
代码执行顺序为：<br>
1，下载数据集<br>
2，运行reader.py文件，将原数据集保存为.tfrecords文件，方便程序的高效读取<br>
3，运行model.py文件，训练模型.<br>

以下是原链接的readme说明。<br>
Implementation of the paper [Attention-over-Attention Neural Networks for Reading Comprehension](https://arxiv.org/abs/1607.04423) in tensorflow

Some context on [my blog](http://olavnymoen.com/2016/10/30/attention-over-attention)

Reading comprehension for cloze style tasks is to remove word from an article summary, then read the article and try to infer the missing word. This example works on the CNN news dataset.

With the same hyperparameters as reported in the paper, this implementation got an accuracy of 74.3% on both the validation and test set, compared with 73.1% and 74.4% reported by the author.

To train a new model: `python model.py --training=True --name=my_model`

To test accuracy: `python model.py --training=False --name=my_model --epochs=1 --dropout_keep_prob=1`

Note that the tfrecords and model files are stored with [git lfs](https://git-lfs.github.com/) 

Raw data for use with `reader.py` to produce .tfrecords files was downloaded from [http://cs.nyu.edu/~kcho/DMQA/]

Interesting parts
- Masked softmax implementation
- Example of batched sparse tensors with correct mask handling
- Example of pointer style attention
- Test/validation split part of the tf-graph
