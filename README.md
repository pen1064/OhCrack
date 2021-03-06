# OhCrack
Road crack detection with transfer learning of Retinanet 
1. The dataset consists of different types of road cracks, is imbalanced 
<img width="227" alt="image" src="https://user-images.githubusercontent.com/45325095/166853793-1895d8c1-6b20-49e0-927a-95cf1d52f933.png">
More descriptions of different types of road cracks can be found in this paper [1]:
<img width="137" alt="image" src="https://user-images.githubusercontent.com/45325095/166854237-a4fb69ad-2bb0-4aa0-8e1e-10dfccbb8a72.png">


2. Transfer learning from Retinanet \
  2.1 Use Resnet50 as backbone, 5 feature pyramid layers are then feed into classification and regression subnets\
  2.2 The Resnet is not forzen, all 5 layers are traiable aiming to improve the classification accuracy for D10 - Linear Crack\
  2.3 Change the number of classes to fit this purpose (num_class = 7), num_classes affect the classification subnet, but not the regression subnet
  
3. Finetuning 

    Initial performace was not great in particular the D10 class. Attempt was made to improve it\
    3.1 Include 4 more boxes with different aspect ratio (0.1, 0.2, 4, 6) to cover more ranges 

4. Train for 94 epches 
AP for each class at different IoU\

| Classes | IoU0.5 | IoU0.75|
| --- | --- | --- |
| D00 | 86.0 %| 79.7 %|
| D10 | 81.3 %| 70.1 %|
| D20 | 84.8 %| 82.2 %|
| D40 | 92.5 %| 82.1 %|
| D43 | 94.6 %| 95.3 %|
| D44 | 87.7 %| 83.6 %|
| D50 | 97.8 %| 89.3 %|

![image](https://user-images.githubusercontent.com/45325095/166853678-ad6c5d53-ed30-4191-8d26-2e5587520ebc.png)

Reference:
1. H. Maeda, Y. Sekimoto, T. Seto, T. Kashiyama, H. Omata. Road Damage Detection Using Deep Neural Networks with Images Captured Through a Smartphone. 2018
