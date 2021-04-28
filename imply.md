## 使用nnUNet
1. 合成符合要求的数据集
    1. 数据集：
    ```
    nnUNet_raw_data_base/nnUNet_raw_data/Task002_Heart
    ├── dataset.json
    ├── imagesTr
    │   ├── la_003_0000.nii.gz
    │   ├── la_004_0000.nii.gz
    │   ├── ...
    ├── imagesTs
    │   ├── la_001_0000.nii.gz
    │   ├── la_002_0000.nii.gz
    │   ├── ...
    └── labelsTr
        ├── la_003.nii.gz
        ├── la_004.nii.gz
        ├── ...
    ```
    其中： `imageTr`代表包含原始影像文件的文件夹。命名方式为`XXX_id_modalid`,XXX是任务名字，如'BraTS'，id是影像编号，modalid是针对多模态影像的id，如BraTS数据集中，T1c模态设置为0001,Flair模态设置为0002。以此类推。

    2. dataset.json文件的生成
    ```
    { 
     "name": "PROSTATE", 
     "description": "Prostate transitional zone and peripheral zone segmentation",
     "reference": "Radboud University, Nijmegen Medical Centre",
     "licence":"CC-BY-SA 4.0",
     "relase":"1.0 04/05/2018",
     "tensorImageSize": "4D",
     "modality": { 
       "0": "T2", 
       "1": "ADC"
     }, 
     "labels": { 
       "0": "background", 
       "1": "PZ", 
       "2": "TZ"
     }, 
     "numTraining": 32, 
     "numTest": 16,
     "training":[{"image":"./imagesTr/prostate_16.nii.gz","label":"./labelsTr/prostate_16.nii.gz"},{"image":"./imagesTr/prostate_04.nii.gz","label":"./labelsTr/prostate_04.nii.gz"},...], 
     "test": ["./imagesTs/prostate_08.nii.gz","./imagesTs/prostate_22.nii.gz","./imagesTs/prostate_30.nii.gz",...]
     }
     ```
     样例如上。