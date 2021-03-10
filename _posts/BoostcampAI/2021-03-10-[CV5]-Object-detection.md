---
title: "[CV5] Object Detection"
subtitle: 
tags: [CV, object detection , R-CNN, Fast R-CNN, Faster R-CNN, YOLO, SSD] 

---

Boostcamp Day 33. 2021-03-10.
DAY33 TIL

# Computer Vision - Object detection

### Contents
1. Object Detection.
2. Two-stage detector (R-CNN family)
    - R-CNN
    - Fast R-CNN
    - Faster R-CNN
3. Single-stage detector.
    - YOLO
    - SSD
4. Single-stage detector vs. two-stage detector.
    - Focal loss
    - RetinaNet
5. Detection with Transformer.

<br>

## Intro
영상 내에 존재하는 객체를 인식하는 방법은 픽셀 마다의 클래스를 분류하는 segmentation 뿐만 아니라 물체 하나하나마다 bounding box 단위의 예측도 있습니다.

이러한 task를 object detection이라고 하며 자율주행, CCTV 등 다양한 분야에 활용되고 있습니다.

Object detection을 위한 모델은 크게 one-stage detector와 two-stage detector로 구분할 수 있는데 시대의 흐름을 따라 각각의 모델들의 발전사를 소개합니다.  

<br>

# 1. Object Detection
> Object Detection = Segmentation + Imgae Classification + Box Localization

객체 검출(Object Detection)은 Image에 담긴 정보들을 효과적으로 특정하고 분류하기 위한 방법들을 아우르는 방법론이라고 보면된다. 이걸 하기 위해서는 여러가지 방법이 있겠지만 Fundamental image recognition tasks로는  
- Semantic Segmentation
- Instance Segmentation
- Panoptic Segmentation


![Kirillov-CVPR2019](/assets/bcimg/CV/Kirillov-CVPR2019.PNG "Kirillov-CVPR2019")

그래서 주로 Autonomous Driving(자율주행), OCR(Optical Character Recognition) Task 등이 대표적인 Object Detection의 활용이라고 보면 된다.

<br>

# 2. Two-stage Detector
## 2.0 Traditional Methods - hand crafted techniques
Deep Learning전의 전통적인 방식으로 이미지를 인식하는 방법들을 간단히 알아보자면
- Gradient-based detector(e.g., HOG, SVM)
    - 이미지에서 Vector값들을 계산해서 기울기를 줬다 뺏다 하면서 연결된 부위를 찾는 방법이 있었다.
    - HOG - Histogram of Oriented Gradients
    - SVM - Support Vector Machine
- Selective Search
    - Segmentation을 하는건데 처음엔 심하게 많이 Box를 치고 공통되는 부분을 합쳐나가면서 objects를 탐지하는 방법.
    1. Over-segmentation
    2. Iteratively merging similar regions
    3. Extracting candidate boxes from all remaining segmentations

## 2.1 R-CNN
> Directly leverage image classification networks for objects detection.  
이미지 분류 네트워크를 직접 활용해서 객체검츨을 한다.

![Girshick-CVPR2014](/assets/bcimg/CV/Girshick-CVPR2014.PNG "Girshick-CVPR2014")

<br>

## 2.2 Fast R-CNN
> Recycle a pre-computed feature for multiple object detection.

![Girshick-ICCV2015](/assets/bcimg/CV/Girshick-ICCV2015.PNG "Girshick-ICCV2015")

1. Conv. feature map `from the original image`
2. Rol(Region of Interest) feature extraction from the feature map through Rol pooling
3. Class and box prediction for each Rol

<br>

## 2.3 Faster R-CNN
> End-toend object detection by neural region proposal.












<br><br>

## Futher Question
- (1) Focal loss는 object detection에만 사용될 수 있을까요?  
- (2) CornerNet/CenterNet은 어떤 형식으로 네트워크가 구성되어 있을까요?


## Further Reading


## Reference

- bootcamp AI Tech pdf.  
- NAVER Connect Foundation.

