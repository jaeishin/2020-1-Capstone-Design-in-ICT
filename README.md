# 2020-AR-DR-using-camera-pose-estimation-and-image-inpainting

AR/DR in images using camera pose estimation and image inpainting
카메라 포즈 추정과 인페인팅을 이용한 AR/DR


- 2020/1/1~2020/6/30일까지 진행한 졸업설계 프로젝트
- 2인 1조로 진행
- 본인은 image inpainting을 기반으로 한 DR를 주로 맡아 진행


1. 프로젝트 주제선정

  관광지에서 촬영한 사진에서 관심없는 타인을 삭제하고 어울리는 사물을 합성해 마치 혼자 찍은 것처럼 보이는 image를 얻자는 아이디어에서 출발!
 
  장소와 상황에 어울리는 가상의 사물을 합성하는 Augmented Reality(AR)와 지우고 싶은 사람을 제거하는 Diminished Reality(DR)의 융합을 제시한다.
  AR의 구현을 위한 카메라 포즈 행렬은 Colmap을 사용해 취득, 가상 사물의 합성을 자연스럽고 입체감 있게 표현하기 위해 Phong reflection model을 사용
  DR의 구현을 위해 자동 human inpainting tool을 구현함
  
2. DR 

  << HUMAN INPAINTING TOOL >>
  
   1. Mask RCNN모델을 사용해 image안에서 사람을 감지
      Mask RCNN을 선택한 이유
      - Faster RCNN기반, instance 단위 segmentation 취득에 용이
      
    - human detection 후, segmentation, bounding box 취득
   
   2. 지우고 싶은 사람을 선택 
   
   3. Deepfill v2 기반 재학습 모델을 통해 선택한 사람을 삭제하고 inpainting
    - GAN based Deepfill v2의 pre trained model사용
    
   4. Homography inpainting(refine 과정)
    - 3번 과정의 inpainting 결과의 정확도가 낮을 시에 homography를 통한 inpainting을 적용함으로써 refine과정 구현
    
      Homography 행렬이란?
      - 한 평면을 다른 평면에 projection할 시, 투영되는 대응점 사이에 성립하는 일정한 변환관계
      
      
      Homography 행렬을 취득하기 위한 background image를 먼저 취득
      
      - 이들 중 refine 목표 image와 matching 되는 feature이 개수가 가장 많은 image를 background image로 선정
      - feature의 개수는 SIFT알고리즘 사용
      - SIFT로 추출한 feature의 개수 중 ratio test를 거쳐 good features를 추려내고 이 개수가 가장 많은 image를 선정
      
3. 결과 
