# What's Your Name?

>Campus Strays Recognizer
>Computer Vision Final Project

## Introduction
We investigate convolution neural network as a general-purpose solution of the object-classification problems. These networks do learning a mapping from input images to outputs labels. This makes us possible to do recognition from a large amount of different objects in real life. In this work, we present a deep model that can accurately identify the most-known campus stray dogs in NTHU by given input photos. The dataset is collected by Carelife Club and ourselves. Our experiments also demonstrate how quality each pre-trained model performs in feature-extraction stage.

## Technical part

* ImageFolder
ImageFolder which comes from torchvision library, is a generic method of data loading and preprocessing. Since we have 9 classes of strays, meaning that we have 9 labels, we can just create 9 folders and put the same genres of images into each kind of folder. The loader will automatically arrange images and finish labeling according to each name of folder in alphabetical order. Therefore our label 0 is a-bye, label 1 is a-gan, and so on.

* DenseNet
In the field of the computer vision, CNN has become the most mainstream method. DenseNet is constructed under this structure and won the Best Paper Award in CVPR 2017. In comparison with ResNet, it not only saves the number of parameters but also reduces calculation amount.

After preprocessing, we use ImageFolder to load data and automatically classify each stray label. As for model, we use DenseNet-169 to train and evaluate. Besides, in the training process, we also artificially decrease the learning rate by multiplying 0.1 times every 5000 training steps.

## Experiments


* Result
![](https://i.imgur.com/g5yVUKy.png)

* Confusion Matrix
![](https://i.imgur.com/auSOkC4.png)

## Requirements

* Python 3.6
* PyTorch 0.4.1


## Usage
1. Clone the project
    ```
    $ git clone https://github.com/Yun-Jung/CV_final.git
    ```
2. Into the folder
    ```
    $ cd CV_final
    ```

3. Train
    ```
    $ python train.py -d=./data/processed -c=./checkpoints
    ```

4. Evaluate
    ```
    $ python eval.py ./checkpoints/model-XXXXXXXXXXXX-XXXXX.pth -d=./data/processed
    ```

5. Infer
    ```
    $ python infer.py ./images/dog.jpg -c=./checkpoints/model-XXXXXXXXXXXX-XXXXX.pth
    ```
