# Painting-Battle 
## 누구의 그림이 실제와 더 비슷할까?
### Contents
1. Description
2. Example Result
3. Model 
4. References
5. License
---
### Description
#### Painting Battle에 대한 전반적인 설명
* 해당 프로젝트는 코랩에서 진행되었다.
* cifar10 datasets을 이용하여 모델을 학습시켰다.
* 그 모델이 플레이어가 그린 그림의 이미지를 예측한 결과를 점수로 반환하여 플레이어 간 점수를 겨루는 게임
#### Painting Battle 플레이 방법
1. 플레이 전 airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck 총 10가지 중 한가지 씩 선택하여 그린 그림을 이미지 파일로 저장한 후 각 이미지 파일의 경로를 코드에 입력  
<img src="Description/p1_path.JPG" width="30%"> <img src="Description/p2_path.JPG" width="30%">
2. player1, player2가 각각 그린 그림의 주제에 대해 입력 ( 잘못된 입력이 왔을 경우 : 올바른 입력을 할 때까지 재입력 수행 )
<img src="Description/player1 입력.JPG" width="60%"> <img src="Description/player2 입력.JPG" width="60%">  <img src="Description/재입력.JPG" width="60%">  
3. cifar10 datasets을 통해 학습한 모델이 플레이어 각각의 그림을 예측, 그 결과를 플레이어의 점수로 환산 후, 게임의 결과가 나옴  
**점수 환산 방법**  
플레이어가 그린 그림의 주제와 모델이 가장 높은 확률로 예측한 그림의 주제가 일치하면 +50점  
플레이거가 그린 그림의 주제와 모델이 가장 높은 확률로 예측한 그림의 주제가 불일치하면 +0점  
그 후 플레이어가 그린 그림의 주제로 모델이 예측한 확률 * 100 을 추가 점수로 부여 (소수점 첫째자리에서 반올림 진행)  
ex) player1 자동차를 그림 -> 모델이 자동차로 예측함 + 약 68%의 정확성을 가짐 = 약118점
---
### Example Result

**업로드한 그림이 색칠이 되어야 보다 정확한 결과를 얻을 수 있음  
주의 - 실제 이미지 datasets을 통해 학습한 모델로 그림을 평가하는 것이므로 실제 묘사 그림에 대한 결과가 좋음**  
각 player의 그림과 그 그림에 대한 예측 결과를 보여줌 - 게임의 승자와 플레이어 간의 점수 차를 보여줌
 
---
### Model
* [kaggle에서 제공하는 cifar10 datasets](https://www.kaggle.com/datasets/oxcdcd/cifar10)을 CNN(Convoutional Neural Networks)을 이용하여 모델을 학습시킴
* 모델 구성시, [정확도를 73% 갖는 오픈소스의 코드](https://www.kaggle.com/code/fahdseddik/cifar10-cnn-73)의 기본적인 model 및 layer 참조
  * 정확도를 더 높이기 위하여 코드를 제작성
  * ImageDataGenerator를 통해 이미지를 증강
  * hidden layer 및 Dropout, BatchNormalization 추가
  <img src="Model/layer구성.JPG" width="40%"> 
* Performace  
정확도 약 80%를 가짐 <img src="Model/Epoch.JPG" width="100%">  <img src="Model/Test_Accuracy.JPG" width="80%"> 
<img src="Model/Accuracy_Trend.JPG" width="45%"> <img src="Model/Loss_Trend.JPG" width="45%">
---
### References
* [정확도를 73% 갖는 오픈소스의 코드](https://www.kaggle.com/code/fahdseddik/cifar10-cnn-73) - model의 기본적인 layer 구성, 틀 등을 참조
---
### License
MIT License
