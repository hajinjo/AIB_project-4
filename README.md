# CNN을 활용한 손글씨 인식 미니 계산기


### 주제 선정  

딥러닝 파트에서 이미지 처리 부분을 더 공부해보고 싶어서 CNN 모델 활용하는 주제선정 

손으로 쓴 수식을 인식해 계산해주는 어플을 생각 

현재 수식을 입력하면 정답을 알려주는 것까지 구현완료 

후에 데이터셋을 더 많이 구해서 발전시킬 수 있을 듯 

### 데이터 셋

0~9까지 아라비아 숫자 및 사칙연산자 총 85,709개 손글씨 이미지

### 모델 학습 및 평가 
두 개의 Convolution층을 사용한 간단한 CNN 모델 구축 

![스크린샷 2021-11-23 오후 5 59 47](https://user-images.githubusercontent.com/83392231/142996945-dc7491d9-b850-4fa3-bf36-6406e3012019.png)

**학습 결과**

![스크린샷 2021-11-23 오후 6 10 55](https://user-images.githubusercontent.com/83392231/142997269-65b85fd9-7685-4048-a8f4-1aca11d24fdc.png)

### 예측 

이미지 안의 요소 분리 작업 

- 계산을 위해 예측할 이미지를 각각 숫자와 연산자로 분리하는 과정 필요

- 값이 있는 열을 찾기 위해 가로열에서 0이 아닌 값이 있는 연속열들을 찾아서 분리

- 분리한 요소들을 전처리 후 모델 인풋에 맞춰 리사이즈

![스크린샷 2021-11-23 오후 6 12 22](https://user-images.githubusercontent.com/83392231/142997515-82bc9120-a312-411e-bddd-86c00e4c9c36.png)

![스크린샷 2021-11-23 오후 6 12 36](https://user-images.githubusercontent.com/83392231/142997519-3c39c0c0-7fbb-42c6-85c0-fc33cea5a507.png)

## 결과 

### Success

input :  ![test](https://user-images.githubusercontent.com/83392231/143000014-284d5fce-c4fa-4849-974d-57430214df5a.jpg)

output :![스크린샷 2021-11-23 오후 6 06 00](https://user-images.githubusercontent.com/83392231/142996615-424e9f4b-d80d-4047-ae28-fdcbb219a7f5.png)

### fail 

input :  ![스크린샷 2021-11-23 오후 6 22 24](https://user-images.githubusercontent.com/83392231/142999028-d6180b9e-ccd6-46a9-b106-626c0c5ef0d5.png)

output :![스크린샷 2021-11-23 오후 6 22 35](https://user-images.githubusercontent.com/83392231/142999026-9dd14fa7-f21a-498f-9684-d9fd9aa2dfb1.png)

9를 4로 인식해서 실패

데이터 셋에서 가져온 숫자 9와 4   ![스크린샷 2021-11-23 오후 6 22 43](https://user-images.githubusercontent.com/83392231/142999022-5f87e27e-e039-4107-89c7-7c2babdd416d.png)

사람이 보기에도 악필이어서 헷갈리는 숫자는 모델도 헷갈려 함 

### 보완할점 

- 위의 실패 케이스처럼 4&9, 0&6 처럼 비슷하게 생긴 숫자는 예측에 종종 실패 

더 많은 데이터로 학습 시키고 실패시 마다 모델을 업데이트 해나갈 수 있게 만들기 

- 다양한 계산식 불가 

대량의 손글씨 데이터를 구하기가 어려움 데이터를 어디서 구할 수 있을지 좀 더 고민 필요 


