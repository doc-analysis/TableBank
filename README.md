# TableBank

**\*\*\*\*\* We randomly split the train/val/test sets and re-train both of the Table Detection and Table Structure Recognition models using Detectron2 and OpenNMT tools. The benchmark results, the MODEL ZOO, and the download link of TableBank have been updated. \*\*\*\*\***

**\*\*\*\*\* A new benchmark dataset DocBank ([Paper](https://arxiv.org/abs/2006.01038), [Repo](https://github.com/doc-analysis/DocBank)) is now available for document layout analysis \*\*\*\*\***

**\*\*\*\*\* Our data can only be used for research purpose \*\*\*\*\***

**\*\*\*\*\* Our paper has been accepted in [LREC 2020](https://lrec2020.lrec-conf.org/en/conference-programme/accepted-papers/) \*\*\*\*\***

TableBank is a new image-based table
detection and recognition dataset built with novel
weak supervision from Word and Latex documents
on the internet, contains 417K high-quality
labeled tables.

## Introduction
To address the need for a standard open domain table
benchmark dataset, we propose a novel weak supervision approach
to automatically create the TableBank, which is orders
of magnitude larger than existing human labeled datasets for
table analysis. Distinct from traditional weakly supervised
training set, our approach can obtain not only large scale but
also high quality training data.

Nowadays, there are a great
number of electronic documents on the web such as Microsoft
Word (.docx) and Latex (.tex) files. These online documents
contain mark-up tags for tables in their source code by nature.
Intuitively, we can manipulate these source code by adding
bounding box using the mark-up language within each document.
For Word documents, the internal Office XML code
can be modified where the borderline of each table is identified.
For Latex documents, the tex code can be also modified
where bounding boxes of tables are recognized. In this
way, high-quality labeled data is created for a variety of domains
such as business documents, official fillings, research
papers etc, which is tremendously beneficial for large-scale
table analysis tasks.

The TableBank dataset totally consists of 417,234 high
quality labeled tables as well as their original documents in
a variety of domains.

### Statistics of TableBank
#### Based on the number of tables
| Task                        | Word    | Latex   | Word+Latex |
|-----------------------------|---------|---------|------------|
| Table detection             | 163,417 | 253,817 | 417,234    |
| Table structure recognition | 56,866  | 88,597  | 145,463    | 

#### Based on the number of images
| Task                        | Word    | Latex   | Word+Latex |
|-----------------------------|---------|---------|------------|
| Table detection             | 78,399  | 200,183 | 278,582    |
| Table structure recognition | 56,866  | 88,597  | 145,463    |

#### Statistics on Train/Val/Test sets of Table Detection
| Source | Train  | Val   | Test |
|--------|--------|-------|------|
| Latex  | 187199 |  7265 | 5719 |
| Word   |  73383 |  2735 | 2281 |
| Total  | 260582 | 10000 | 8000 |

#### Statistics on Train/Val/Test sets of Table Structure Recognition
| Source | Train  | Val   | Test |
|--------|--------|-------|------|
| Latex  |  79486 |  6075 | 3036 |
| Word   |  50977 |  3925 | 1964 |
| Total  | 130463 | 10000 | 5000 |


## License
TableBank is released under the [Attribution-NonCommercial-NoDerivs License](https://creativecommons.org/licenses/by-nc-nd/4.0/). You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may not use the material for commercial purposes. If you remix, transform, or build upon the material, you may not distribute the modified material.



## Task Definition

### Table Detection
Table detection aims to locate tables using bounding boxes
in a document. 
Given a document page in the image format,
generating several bounding box that represents the
location of tables in this page.

### Table Structure Recognition
Table structure recognition aims to identify the row and column
layout structure for the tables especially in non-digital
document formats such as scanned images.
Given a table in the image format,
generating an HTML tag sequence that represents the
arrangement of rows and columns as well as the type of table
cells.

## Baselines
To verify the effectiveness of Table-Bank,
we build several strong baselines using the state-of-the-art
models with end-to-end deep neural networks. The
table detection model is based on the Faster R-CNN [Ren
et al., 2015] architecture with different settings. The table
structure recognition model is based on the encoder-decoder
framework for image-to-text.
### Data and Metrics
To evaluate
table detection, we sample 18,000 document images from
Word and Latex documents, where 10,000 images
for validation and 8,000 images for testing. Each sampled image
contains at least one table. Meanwhile, we also evaluate
our model on the ICDAR 2013 dataset to verify the effectiveness
of TableBank. To evaluate table structure recognition,
we sample 15,000 table images from
Word and Latex documents, where 10,000 images
for validation and 5,000 images for testing. 
For table detection, we calculate the precision, recall
and F1 in the way described in our paper, where
the metrics for all documents are computed by summing up
the area of overlap, prediction and ground truth. For table
structure recognition, we use the 4-gram BLEU score as the
evaluation metric with a single reference.

### Table Detection
We use the open-source framework Detectron2
[Wu et al., 2019] to train models on the TableBank.
Detectron2 is a high-quality and high-performance codebase
for object detection research, which supports many state-of-the-art
algorithms. In this task, we use the Faster R-CNN algorithm
with the ResNeXt [Xie et al., 2016] as the backbone
network architecture, where the parameters are pre-trained on
the ImageNet dataset. All baselines are trained using 4 V100
NVIDIA GPUs using data-parallel sync SGD with a minibatch
size of 20 images. For other parameters, we use the
default values in Detectron2. During testing, the confidence
threshold of generating bounding boxes is set to 90%.

|      Models      |    Word   |        |        |   Latex   |        |        | Word+Latex |        |        |
|:----------------:|:---------:|:------:|:------:|:---------:|:------:|:------:|:----------:|:------:|:------:|
|                  | Precision | Recall |   F1   | Precision | Recall |   F1   |  Precision | Recall |   F1   |
|    X101(Word)    |   0.9352  | 0.9398 | 0.9375 |   0.9905  | 0.5851 | 0.7356 |   0.9579   | 0.7474 | 0.8397 |
|    X152(Word)    |   0.9418  | 0.9415 | **0.9416** |   0.9912  | 0.6882 | 0.8124 |   0.9641   | 0.8041 | 0.8769 |
|    X101(Latex)   |   0.8453  | 0.9335 | 0.8872 |   0.9819  | 0.9799 | 0.9809 |   0.9159   | 0.9587 | 0.9368 |
|    X152(Latex)   |   0.8476  | 0.9264 | 0.8853 |   0.9816  | 0.9814 | **0.9815** |   0.9173   | 0.9562 | 0.9364 |
| X101(Word+Latex) |   0.9178  | 0.9363 | 0.9270 |   0.9827  | 0.9784 | 0.9806 |   0.9526   | 0.9592 | **0.9559** |
| X152(Word+Latex) |   0.9229  | 0.9266 | 0.9247 |   0.9837  | 0.9752 | 0.9795 |   0.9557   | 0.9530 | 0.9543 |

### Table Structure Recognition
For table structure recognition, we use the open-source
framework OpenNMT [Klein et al., 2017] to train the image-to-text model.
OpenNMT is mainly designed for neural
machine translation, which supports many encoder-decoder
frameworks. In this task, we train our model using the image-to-text
method in OpenNMT. The model is also trained using
4 V100 NVIDIA GPUs with the learning rate of 1
and batch size of 24. For other parameters,
we use the default values in OpenNMT.

|           Models           |  Word | Latex | Word+Latex |
|:--------------------------:|:-----:|:-----:|:----------:|
|    Image-to-Text (Word)    | 59.18 | 69.76 |    65.75   |
|    Image-to-Text (Latex)   | 51.45 | 71.63 |    63.08   |
| Image-to-Text (Word+Latex) | **69.93** | **77.94** |    **74.54**   |

## Model Zoo

The trained models are available for download in the [TableBank Model Zoo](MODEL_ZOO.md).

<!-- ## Quick Start
Here is a pipeline to test pretrained model and visualize the performance of Table Detection task. [Table Detection](TestPretrainedModel.md). -->

## Get Data and Leaderboard
<!-- **Because some data has copyright issues and should not be released, we filtered all the data and excluded them. We also retrain all the baseline model on the changed dataset and list them on the leaderboard website.** -->


**\*\*Please DO NOT re-distribute our data.\*\***

If you use the corpus in published work, please cite it referring to the "Paper and Citation" Section.

The annotations and original document pictures of the TableBank dataset **can be download from the [TableBank dataset homepage](https://doc-analysis.github.io/tablebank-page/index.html)**.



<!-- The leaderboard website is [https://doc-analysis.github.io/](https://doc-analysis.github.io/). If you would like to add a paper that reports a number at or above the current state of the art, email [Minghao Li](mailto:liminghao1630@buaa.edu.cn). -->

<!-- ### Statistics of TableBank (Removing copyright protection data)
| Task                        | Word    | Latex   | Word+Latex |
|-----------------------------|---------|---------|------------|
| Table detection             | 101,889 | 253,817 | 355,706    |
| Table structure recognition | 56,866  | 88,597  | 145,463    | -->



## Paper and Citation
https://arxiv.org/abs/1903.01949
```
@misc{li2019tablebank,
    title={TableBank: A Benchmark Dataset for Table Detection and Recognition},
    author={Minghao Li and Lei Cui and Shaohan Huang and Furu Wei and Ming Zhou and Zhoujun Li},
    year={2019},
    eprint={1903.01949},
    archivePrefix={arXiv},
    primaryClass={cs.CV}
}
```

## References

- [Ren et al., 2015] Shaoqing Ren, Kaiming He, Ross B. Girshick,
    and Jian Sun. Faster R-CNN: towards real-time
    object detection with region proposal networks. CoRR,
    abs/1506.01497, 2015.
- [Gilani et al., 2017] A. Gilani, S. R. Qasim, I. Malik, and
    F. Shafait. Table detection using deep learning. In Proc. of
    ICDAR 2017, volume 01, pages 771–776, Nov 2017.
- [Wu et al., 2019] Y Wu, A Kirillov, F Massa, WY Lo, R Girshick. [Detectron2](https://github.com/facebookresearch/detectron2)[J]. 2019.
- [Xie et al., 2016] Saining Xie, Ross B. Girshick, Piotr
    Doll´ar, Zhuowen Tu, and Kaiming He. Aggregated residual
    transformations for deep neural networks. CoRR,
    abs/1611.05431, 2016.
- [Klein et al., 2017] Guillaume Klein, Yoon Kim, Yuntian
    Deng, Jean Senellart, and Alexander M. Rush. Open-NMT:
    Open-source toolkit for neural machine translation.
    In Proc. of ACL, 2017.]
