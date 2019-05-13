# TableBank

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
| Task                        | Word    | Latex   | Word+Latex |
|-----------------------------|---------|---------|------------|
| Table detection             | 163,417 | 253,817 | 417,234    |
| Table structure recognition | 56,866  | 88,597  | 145,463    |


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
table detection, we sample 2,000 document images from
Word and Latex documents respectively, where 1,000 images
for validation and 1,000 images for testing. Each sampled image
contains at least one table. Meanwhile, we also evaluate
our model on the ICDAR 2013 dataset to verify the effectiveness
of TableBank. To evaluate table structure recognition,
we sample 500 tables each for validation and testing from
Word documents and Latex documents respectively. The entire
training and testing data will be made available to the public
soon. For table detection, we calculate the precision, recall
and F1 in the same way as in [Gilani et al., 2017], where
the metrics for all documents are computed by summing up
the area of overlap, prediction and ground truth. For table
structure recognition, we use the 4-gram BLEU score as the
evaluation metric with a single reference.

### Table Detection
We use the open source framework Detectron
[Girshick et al., 2018] to train models on the TableBank.
Detectron is a high-quality and high-performance codebase
for object detection research, which supports many state-of-the-art
algorithms. In this task, we use the Faster R-CNN algorithm
with the ResNeXt [Xie et al., 2016] as the backbone
network architecture, where the parameters are pre-trained on
the ImageNet dataset. All baselines are trained using 4 P100
NVIDIA GPUs using data parallel sync SGD with a minibatch
size of 16 images. For other parameters, we use the
default values in Detectron. During testing, the confidence
threshold of generating bounding boxes is set to 90%.

| Models                   | Word      |        |        | Latex     |        |        | Word+Latex |        |        |
|--------------------------|-----------|--------|--------|-----------|--------|--------|------------|--------|--------|
|                          | Precision | Recall | F1     | Precision | Recall | F1     | Precision  | Recall | F1     |
| ResNeXt-101 (Word)       | 0.9496    | 0.8388 | 0.8908 | 0.9902    | 0.5948 | 0.7432 | 0.9594     | 0.7607 | 0.8486 |
| ResNeXt-152 (Word)       | 0.9530    | 0.8829 | **0.9166** | 0.9808    | 0.6890 | 0.8094 | 0.9603     | 0.8209 | 0.8851 |
| ResNeXt-101 (Latex)      | 0.8288    | 0.9395 | 0.8807 | 0.9854    | 0.9760 | 0.9807 | 0.8744     | 0.9512 | 0.9112 |
| ResNeXt-152 (Latex)      | 0.8259    | 0.9562 | 0.8863 | 0.9867    | 0.9754 | **0.9810** | 0.8720     | 0.9624 | 0.9149 |
| ResNeXt-101 (Word+Latex) | 0.9557    | 0.8403 | 0.8943 | 0.9886    | 0.9694 | 0.9789 | 0.9670     | 0.8817 | 0.9224 |
| ResNeXt-152 (Word+Latex) | 0.9540    | 0.8639 | 0.9067 | 0.9885    | 0.9732 | 0.9808 | 0.9657     | 0.8989 | **0.9311** |

### Table Structure Recognition
For table structure recognition, we use the open source
framework OpenNMT [Klein et al., 2017] to train the image-to-text model.
OpenNMT is mainly designed for neural
machine translation, which supports many encoder-decoder
frameworks. In this task, we train our model using the image-to-text
method in OpenNMT. The model is also trained using
4 P100 NVIDIA GPUs with the learning rate of 0.1
and batch size of 24. For other parameters,
we use the default values in OpenNMT.

| Models                     | Word   | Latex  | Word+Latex |
|----------------------------|--------|--------|------------|
| Image-to-Text (Word)       | **0.7507** | 0.6733 | 0.7138     |
| Image-to-Text (Latex)      | 0.4048 | **0.7653** | 0.5818     |
| Image-to-Text (Word+Latex) | 0.7121 | 0.7647 | **0.7382**     |

## Model Zoo

The trained models available for download in the [TableBank Model Zoo](MODEL_ZOO.md).

## Quick Start
Here is a pipeline to test pretrained model and visualize the performance of Table Detection task. [Table Detection](TestPretrainedModel.md).

## Get Data and Leaderboard
**Because some data has copyright issues and should not be released, we filtered all the data and excluded them. We also retrain all the baseline model on the changed dataset and list them on the leaderboard website.**

Please fill this [form](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbRw1hSTX2waZIoerSk1J6CyNUMTRCUEZCR0lVOVZaTVhLUFVJTjhJUkdXSi4u). If the review is approved, the download link will be sent to your email address. 

The leaderboard website is [https://doc-analysis.github.io/](https://doc-analysis.github.io/). If you would like to add a paper that reports a number at or above the current state of the art, email [Minghao Li](mailto:liminghao1630@buaa.edu.cn).

### Statistics of TableBank (Removing copyright protection data)
| Task                        | Word    | Latex   | Word+Latex |
|-----------------------------|---------|---------|------------|
| Table detection             | 101,889 | 253,817 | 355,706    |
| Table structure recognition | 56,866  | 88,597  | 145,463    |

## Paper and Citing
https://arxiv.org/abs/1903.01949
```
@article{li2019tablebank,
  title={TableBank: Table Benchmark for Image-based Table Detection and Recognition},
  author={Li, Minghao and Cui, Lei and Huang, Shaohan and Wei, Furu and Zhou, Ming and Li, Zhoujun},
  journal={arXiv preprint arXiv:1903.01949},
  year={2019}
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
- [Girshick et al., 2018] Ross Girshick, Ilija Radosavovic,
    Georgia Gkioxari, Piotr Doll´ar, and Kaiming He. [Detectron](
    https://github.com/facebookresearch/detectron).
    2018.
- [Xie et al., 2016] Saining Xie, Ross B. Girshick, Piotr
    Doll´ar, Zhuowen Tu, and Kaiming He. Aggregated residual
    transformations for deep neural networks. CoRR,
    abs/1611.05431, 2016.
- [Klein et al., 2017] Guillaume Klein, Yoon Kim, Yuntian
    Deng, Jean Senellart, and Alexander M. Rush. Open-NMT:
    Open-source toolkit for neural machine translation.
    In Proc. of ACL, 2017.]