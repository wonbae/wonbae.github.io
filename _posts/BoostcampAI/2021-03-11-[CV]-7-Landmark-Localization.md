---
title: "[CV] 7.Landmark Localization"
subtitle: 
tags: [CV, Landmark Localization, Hour glass] 

---

Boostcamp Day 34. 2021-03-11.
DAY34 TIL

# Landmark Localization - Hour glass

### Contents
- What is landmark localization?
- Coordinate regression vs. heatmap classification
- Hourglass network

<br>

## Intro
단순히 픽셀 마다의 클래스를 분류하는 semantic segmentation은 동일한 클래스에 속하는 개별 물체를 구분하지 못합니다. 이와 달리 instance segmentation은 영상 내에 동일한 물체가 여러 개 존재하는 경우에 각각의 물체를 구분하며 동시에 픽셀 단위의 mask도 예측하는 방법입니다. 그리고 semantic segmentation과 instance segmentation을 결합하여 더욱 복잡한 task인 panoptic segmentation을 소개합니다.

또 다른 물체를 인식하는 방법에는 각 물체를 대표하는 점들을 예측하는 것이 있습니다. 이러한 task를 landmark localization이라고 하며 사람의 동작을 인식하는 human pose estimation에 주로 사용되고 있습니다. Landmark localization을 대표하는 모델인 hourglass를 위주로 해당 task를 소개합니다.

# What is landmark localization?
- Facial landmark localization
- Human pose estimation

`Landmark Localization` = keypoint estimation (Predicting the coordinates of keypoints)


# Coordinate regression vs. heatmap classification
- coordinate regression : usually inaccurate and biased
- **Heatmap classification** : better performane but high computational cost

- Landmark location to Gaussian heatmap

    - ${G_\sigma(x,y)} = exp(- {(x-x_c)^2 + (y - y_c)^2 \over 2\sigma^2} )$

# Hourglass network
![Newel-ECCV2016](/assets/bcimg/CV/Newel-ECCV2016.PNG "Newel-ECCV2016")

- `Stacked hourglass modules` allow for repeated bottom-up and top-down inference that refines the output of the previous hourglass module.

- CNN과 Pooling을 통해 Down Sampling과정에서 이미지 속 모든 스케일에 관한 정보를 추출해 낸다.

- Upsampling과정에서, 다운샘플링 과정에서 추출한 정보를 토대로 Pixel-wise output을 생성한다.

- Output은 2개의 연속적인 1 * 1 CNN을 거쳐서 결과를 예측한다.

- Hourglass를 여려개를 쌓아서 사용하기도 한다.

# Extentions
- DensePose
    - All pixels -> 3D surface of the human body.
    - `UV map` is a flattened representation of 3D geometry Also, UV map is invariant to motion(i.e., canonical coordinate)  
    - DensePose R-CNN = Faster R-CNN + `3D surface regression branch`
- RetinaFace
    ![Deng-CVPR2020](/assets/bcimg/CV/Deng-CVPR2020.PNG "Deng-CVPR2020")
    - RetinaFace = FPN + Multi-task branches
    (classification, bounding box, 5 point regression, mesh regression)





<br><br>

## Futher Question
(1) Mask R-CNN과 Faster R-CNN은 어떤 차이점이 있을까요? (ex. 풀고자 하는 task, 네트워크 구성 등)
(2) Panoptic segmentation과 instance segmentation은 어떤 차이점이 있을까요?
(3) Landmark localization은 human pose estimation 이외의 어떤 도메인에 적용될 수 있을까요?


## Further Reading


## Reference

- bootcamp AI Tech pdf.  
- NAVER Connect Foundation.

