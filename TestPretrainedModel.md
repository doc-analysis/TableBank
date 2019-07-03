# Table Detection Task

This provides a pipeline to test pretrained model and visualize the performance of Table Detection task.

Table detection aims to locate tables using bounding boxes in a document. Given a document page in the image format, generating several bounding box that represents the location of tables in this page.

The authors pretrained two models (ResNeXt-101 and ResNeXt-152) using the Detectron library. So we need to install Detectron first.

The installation of Detectron is introduced officially [here](https://github.com/facebookresearch/Detectron/blob/master/INSTALL.md). Detectron is based on Caffe2, which is now integrated into Pytorch library now. But be careful that **the operators in detectron has no CPU version, so a GPU system is needed.**. Also, when I'm installing the dependencies according to https://github.com/facebookresearch/Detectron/blob/master/INSTALL.md#detectron by `pip install -r $DETECTRON/requirements.txt`, I
notice that I must use `pip install pyyaml==3.12`  to install a elder version of pyyaml instead of the latest, or I will meet the error `BBOX_XFORM_CLIP: !!python/object/apply:numpy.core`. This issue is posted [here](https://github.com/facebookresearch/Detectron/issues/840). 

The complete commands are 

```
# DETECTRON=/path/to/clone/detectron
git clone https://github.com/facebookresearch/detectron $DETECTRON
pip install pyyaml==3.12
pip install -r $DETECTRON/requirements.txt
cd $DETECTRON && make
python $DETECTRON/detectron/tests/test_spatial_narrow_as_op.py
```

I will experiment on the ResNeXt101 model in the following, while the pipeline for ResNeXt152 is similiar.

You need to download the configuration file and the weights of the model first [here](https://github.com/doc-analysis/TableBank/blob/master/MODEL_ZOO.md#table-detection). In the following, we use `$MODEL_PATH` to denote the downloaded weights and `$CONFIG_MODEL` to denote the configuration file.

Then simply run the commands 

```
python tools/infer_simple.py --cfg $CONFIG_MODEL --output-dir /tmp/detectron-tablebank --image-ext jpg \
    --wts $MODEL_PATH /home/shr/TableBank/data/Sampled_Detection_data/Latex/images
```

where `/home/shr/TableBank/data/Sampled_Detection_data/Latex/images` is the input directory and `jpg` is the input format.

The detected table will be visualized in the directory `/tmp/detectron-tablebank`. By default, if no object can be detected for an input image, there will not be corresponding output file in the target directory. You can add `----always-out` to generate the annotated pdf even if nothing is detected.

