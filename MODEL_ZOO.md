# Model Zoo

## Introduction

The models trained in our baseline are listed below. All models were trained 10 epochs under their respective backbones. Using the pretrained model provided by [Detectron2](https://github.com/facebookresearch/detectron2/blob/master/MODEL_ZOO.md).


## Models

### Table Detection 
The models trained on TableBank are available in the format used by Detectron2. 

|      Models      |    Url   |  Size  |
|:----------------:|:--------:|:------:|
|    X101(Word)    | [Model](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/Word_X101/model_final.pth?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D)/[Config](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/Word_X101/Word_X101.yaml?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D) |  796MB |
|    X152(Word)    | [Model](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/Word_X152/model_final.pth?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D)/[Config](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/Word_X152/Word_X152.yaml?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D) | 1.03GB |
|    X101(Latex)   | [Model](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/Latex_X101/model_final.pth?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D)/[Config](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/Latex_X101/Latex_X101.yaml?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D) |  796MB |
|    X152(Latex)   | [Model](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/Latex_X152/model_final.pth?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D)/[Config](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/Latex_X152/Latex_X152.yaml?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D) | 1.03GB |
| X101(Word+Latex) | [Model](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/All_X101/model_final.pth?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D)/[Config](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/All_X101/All_X101.yaml?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D) |  796MB |
| X152(Word+Latex) | [Model](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/All_X152/model_final.pth?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D)/[Config](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/detection/All_X152/All_X152.yaml?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D) | 1.03GB |

### Table Recognition
The models trained on TableBank are available in the format used by OpenNMT. 

|           Models           |    Url   |  Size  |
|:--------------------------:|:--------:|:------:|
|    Image-to-Text (Word)    | [Model](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/recognition/Recognition_Word.pt?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D) | 49.5MB |
|    Image-to-Text (Latex)   | [Model](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/recognition/Recognition_Latex.pt?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D) | 49.5MB |
| Image-to-Text (Word+Latex) | [Model](https://layoutlm.blob.core.windows.net/tablebank/model_zoo/recognition/Recognition_All.pt?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D) | 49.5MB |
