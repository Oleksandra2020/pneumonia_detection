# Pneumonia Detection

Project in AI course meant to compare various CNN architectures for pneumonia detection.

## Review of related works

The accuracy of pneumonia detection largely depends on the models that are being used. The most commonly used architectures are pretrained ResNet-50, DenseNet-121 and VGG-16.

There may be different ways to represent detection, too. For example, some models produce a binary result if there is pneumonia on an X-ray image or not, but some can also pinpoint the damaged area. In order to do the latter, in CheXNet research ([link](https://arxiv.org/pdf/1711.05225.pdf)) DenseNet-121 is used as the base model and the last fully connected layer is substituted with a layer with a single output, which produces an F1-score of 0.435. ResNet-152 has also been used in pneumonia localization ([link](https://arxiv.org/pdf/1811.08939.pdf)).

There are also other approaches, which use architectures for feature extraction in combination with a classifier for final pneumonia detection. In the research on pneumonia detection based on feature extraction ([link](https://ieeexplore.ieee.org/abstract/document/8869364)), where AUC score is used as the main metric, VGG-16 with KNN is also presented, although its score is not the best (0.68). On the other hand, DenseNet-121 with SVM, DenseNet-169 with SVM and ResNet-50 with SVM showed the best AUC scores of around 0.78-0.8.

Although the results are quite good, there are also limitations. In most cases it is not allowed to use patient’s history, so the detection has to be made only through X-ray images. Second, mostly only the frontal X-rays are being used, while having lateral view available, too, improves accuracy of the model.

## Results

I used pretrained ResNet-50, DenseNet-121 and VGG-16 for pneumonia classification based on Chest X-ray images dataset ([link](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia)) with around 5 thousand X-ray images present for training. The dataset is imbalanced with 3875 pneumonia images and 1341 normal images. Therefore, weighted loss is used.

Results for:

- ResNet-50:

test Loss: 0.3232 Acc: 0.8814

test Precision: 0.8990

test Recall: 0.9128

- DenseNet-121:

test Loss: 0.2722 Acc: 0.8958

test Precision: 0.9114

test Recall: 0.9231

- VGG16:

test Loss: 0.6113 Acc: 0.8478

test Precision: 0.8792

test Recall: 0.8769


We can see that VGG16 does poorly in every metric, while ResNet50 and DenseNet121 are quite similar, except that ResNet50 has greater loss. Therefore the best model based on these metrics is DenseNet121.

## License
[MIT](https://choosealicense.com/licenses/mit/)
