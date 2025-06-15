# 모델 학습에서의 편향(Bias)과 분산(Variance), 두 개념 간의 관계
* 편향 : 한 쪽으로 치우친 정도, 즉 모델 학습에서 예측값과 실제값에 얼마나 가깝거나 먼지 보는 척도
* 분산 : 퍼져있는 정도, 즉 모델 학습에서 예측값과 실제값이 얼마나 흩어져있는지 보는 척도 </br>

<img width="712" alt="Image" src="https://github.com/user-attachments/assets/daaab32f-f8d4-4d28-a475-3460d493239a" /> </br>

> 편향과 분산의 관계
* 편향과 분산은 trade-off 관계로, 반비례하는 경향을 보임
> 이미지 출처
https://medium.com/data-science/understanding-the-bias-variance-tradeoff-165e6942b229
---
# K-Fold 교차 검증에서 K의 값을 선택할 때 고려해야 할 점
> K-Fold 교차 검증이란?
* K개의 데이터 세트를 만들어 K번만큼 각 세트에 학습과 평가를 반복적으로 수행하는 방법
* K-1개의 훈련세트, 1개의 검증세트
  * 이를 통해 K개의 예측 평가를 평균으로 계산하여 평가 결과 값으로 리턴함 </br>
  
<img width="694" alt="Image" src="https://github.com/user-attachments/assets/87766df6-7e34-44a8-8edc-17266264810c" /> </br>

> 고려해야할 점
1. 데이터셋의 크기 : 작으면 많이, 크면 적게
2. 모델 학습 시간 : 훈련을 여러번 할수록 비용 증가
3. 편향과 분산 : K가 작을수록 검증 세트가 커지면서 편향이 커지고 분산은 작아짐 -> 편향과 분산 정도의 조합 고려
> 이미지 출처
https://quantdev.ssri.psu.edu/sites/qdev/files/CV_tutorial.html
