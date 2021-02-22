# 2020-1-Capstone-Desing-in-ICT

## 0. 개요
- AR/DR in images using camera pose estimation and image inpainting
- 카메라 포즈 추정과 인페인팅을 이용한 AR/DR
- 2020/1/1~2020/6/30일까지 진행한 졸업설계 프로젝트
- 2인 1조로 진행
- 본인은 image inpainting을 기반으로 한 DR를 주로 맡아 진행


## 1. 프로젝트 주제선정
- 관광지에서 촬영한 사진에서 관심없는 타인을 삭제하고 어울리는 사물을 합성해 마치 혼자 찍은 것처럼 보이는 image를 얻자는 아이디어에서 출발!

![flow](https://user-images.githubusercontent.com/61179297/108716156-17688200-755f-11eb-915f-c5415b38d4ec.png)

- 장소와 상황에 어울리는 가상의 사물을 합성하는 Augmented Reality(AR)와 지우고 싶은 사람을 제거하는 Diminished Reality(DR)의 융합을 제시한다.
  AR의 구현을 위한 카메라 포즈 행렬은 Colmap을 사용해 취득, 가상 사물의 합성을 자연스럽고 입체감 있게 표현하기 위해 Phong reflection model을 사용
  DR의 구현을 위해 자동 human inpainting tool을 구현함
  
## 2. DR - HUMAN INPAINTING TOOL 제작

### 2-1. tool 동작 순서

    1. Mask RCNN 모델을 사용해 image안에서 사람을 감지
    2. 지우고 싶은 사람 선택
    3. Deepfill v2기반 재학습 모델을 통해 선택한 사람을 삭제하고 inpainting(model inpainting)
    4. Background image와 Homography 행렬을 사용한 inpainting refine과정(homography inpainting)

자세한 설명은 /paper/ARDR_in_images_using_camera_estimation_and_image_inpainting.pptx

## 3. 결과 및 논문
대한전자공학회 포스터 발표논문: /paper/[ieie]ARDR_in_images_using_camera_estimation_and_image_inpainting.pdf
대한전자공학회 포스터 발표영상: /video/[ieie]ARDR_in_images_using_camera_estimation_and_image_inpainting.mp4
프로젝트 발표 유튜브 링크:
https://youtu.be/vc6aueLRqHA
