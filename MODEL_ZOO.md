# Model Zoo

## Introduction

The models trained in our baseline are listed below. All models were trained 20epochs under their respective backbones. Using the pretrained model provided by [detectron](https://github.com/facebookresearch/Detectron/blob/master/MODEL_ZOO.md).


## License

All models available for download through this document are licensed under the [Attribution-NonCommercial-NoDerivs License](https://creativecommons.org/licenses/by-nc-nd/4.0/).

## Models

### Table Detection 
The models trained on TableBank are available in the format used by Detectron. 

- [Without Copyright Data X101](https://conversationhub.blob.core.windows.net/tablebank/model_zoo/Without_copyright/X101/model_final.pkl): Trained ResNeXt101 on latex and word mixed dataset without Copyright data.[[config](https://conversationhub.blob.core.windows.net/tablebank/model_zoo/Without_copyright/X101/config_X101.yaml)]
- [Without Copyright Data X152](https://conversationhub.blob.core.windows.net/tablebank/model_zoo/Without_copyright/X152/model_final.pkl): Trained ResNeXt152 on latex and word mixed dataset without Copyright data.[[config](https://conversationhub.blob.core.windows.net/tablebank/model_zoo/Without_copyright/X152/config_X152.yaml)]

### Table Recognition
The models trained on TableBank are available in the format used by OpenNMT. 

- [Without Copyright Data](https://conversationhub.blob.core.windows.net/tablebank/model_zoo/Recognition_all_without_copyright/model.pt): Trained image-to-markup model on latex and word mixed dataset without Copyright data.