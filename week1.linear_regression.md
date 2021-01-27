---

-   Keyword: Linear Regression, Loss Function, Gradient Descent, Logistic Regression
    
-   Lecture:
    
    [Lecture 2 - Linear Regression and Gradient Descent | Stanford CS229: Machine Learning (Autumn 2018)](https://youtu.be/4b4MUYve_U8)
    
    [Lecture 3 - Locally Weighted & Logistic Regression | Stanford CS229: Machine Learning (Autumn 2018)](https://youtu.be/het9HFqo1TQ)
    

---

### Before reading...

-   parameters = weight: 구해야 할 값
-   label: 주어진 특정 x(i)값에 대한 답 y(i)값을 label이라 부릅니다.
-   classification: 연속된 값을 구하는 regression에 비해, classification은 0(negative class)과 1(positive class) 둘 중 하나를 고르게 됩니다.
-   Supervised Learning Process  
    [##_Image|kage@ABhoh/btqUYF0VkBf/2CXTTaCTYExfVZplsmKuyk/img.png|alignCenter|data-origin-width="808" data-origin-height="758" width="189" height="NaN" data-ke-mobilestyle="widthContent"|||_##]

## Linear Regression

### General Notions

교수님은 supervised learning을 소개하며, X,Y(Training Set)가 있는 상태에서 둘 사이의 관계를 알아보고자 linear regression 을 소개하셨다.

Linear Regression에서의 가장 기본적인 구조를 다음과 같다.

![](https://render.githubusercontent.com/render/math?math=h_%7B%5Ctheta%7D(x)%20%20%3D%20%5Ctheta_%7B0%7D%2B%5Ctheta_%7B1%7Dx_%7B1%7D%2B...%2B%0A%3D%5Csum_%7Bi%3D1%7D%5Ed%20%5Ctheta_%7Bi%7Dx_%7Bi%7D%20%3D%20%7B%5Ctheta%7D%5ETX)

-   h(x): X,Y의 관계를 정의하는 식 (X에서 d개의 feature가 있다고 가정, x\_i는 각각의 (d개의 feature중 i번째) feature 값들을 나타낸다.
-   Parameters

[##_Image|kage@bf2qsa/btqUTmnNddg/Cik0aZkD9KHf639lLktm2K/img.png|alignCenter|data-origin-width="0" data-origin-height="0" width="222" height="NaN" data-ke-mobilestyle="widthContent"|||_##]

즉, **구해야 할 것은 Parameter 인 theta**이다. 완벽한 theta를 구하기 위해

Parameter에 임의로 값을 넣고 → 차이를 확인하고 → 임의값을 수정: 정확한 Parameter로 가는 길

하는 방식으로 이루어진다.

### 차이를 확인하는 방법: Loss Function

Loss function은 다음과 같이 정의될 수 있다.

![](https://render.githubusercontent.com/render/math?math=J(%7B%5Ctheta%7D)%20%3D%20%5Cfrac%7B1%7D%7B2%7D%5Csum_%7Bi%3D1%7D%5En%20%7B(h_%7B%5Ctheta%7D(x%5E%7B(i)%7D)-y%5E%7B(i)%7D)%7D%5E%7B2%7D%20)

여기서 정의된 Loss Function은 X,Y의 차이를 극대화하는 방향으로 작성되며, 이 외에도 다양한 종류가 존재한다.

### 값 수정하기: Gradient Descent

Loss Function에서 정의한 차를 바탕으로 Parameter 값을 재정의해야 한다. 재정의하기 위해서 Gradient Descent Algorithm을 사용한다. 이를 밑에서 보기로 하자.

## Gradient Descent

### **General Notions**

Parameter를 재정의하기 위해 전에 있던 값을 바탕으로 adjust/update 하는 일이 필요하다. 이 algorithm에서는 다음과 같이 정의한다.

![](https://render.githubusercontent.com/render/math?math=%7B%5Ctheta%7D_j%20%3A%3D%20%7B%5Ctheta%7D_j%20-%20%5Calpha%5Cfrac%7B%5Cpartial%7D%7B%5Cpartial%20%7B%5Ctheta%7D_j%7D%20J(%7B%5Ctheta%7D)%20)

-   Parameter: theta들과 알파(: learning rate)

간단하게 말하면, (현재 값) = (이전 값) - (조정 값: alpha) \*(손실함수의 기울기)

(조정 값: alpha)은 임의로 정하여 변동의 가능성이 있고, (손실함수의 기울기)는 급격히 변해야함/조금씩 변해야함을 가르키는 값으로 필자는 해석하였다.

여기서 손실함수의 기울기를 더 자세히 살펴보자.

[##_Image|kage@rmV4q/btqUMavlC3P/EC15WswDRErwk2IKKfgrM0/img.png|alignCenter|data-origin-width="882" data-origin-height="448" width="474" height="NaN" data-ke-mobilestyle="widthContent"|||_##]

이렇게 정리된다면, 위의 Gradient Descent는 다음과 같이 정의된다.

![](https://render.githubusercontent.com/render/math?math=%7B%5Ctheta%7D_j%20%3A%3D%20%7B%5Ctheta%7D_j%2B%5Calpha%20%5C%3B%20(y%5E%7B(i)%7D%20-%20h_%7B%5Ctheta%7D(x%5E%7B(i)%7D))%5C%3Bx_j%5E%7B(i)%7D)

이 규칙을 LMS update rule로 정의한다. 이 update를 바탕으로 Gradient Descent 는 다음과 같이 정의된다.

![](https://render.githubusercontent.com/render/math?math=Repeat%20%5C%3B%20Until%20%5C%3B%20Convergence%5Cleft%5C%7B%7B%5Ctheta%7D_j%20%3A%3D%20%7B%5Ctheta%7D_j%2B%5Calpha%20%5C%3B%20(y%5E%7B(i)%7D%20-%20h_%7B%5Ctheta%7D(x%5E%7B(i)%7D))%5C%3Bx_j%5E%7B(i)%7D%2C%5C%3B(for%20%5C%3B%20every%20%5C%3B%20j)%5Cright%5C%7D)

이를 반복하며 update 하는데, 사실 X는 생각하는 것보다 많은 개수의 데이터를 가지고 있다. 값을 일일이 계산하여 구하는데 굉장히 많은 시간이 소요된다. 이를 극복하기 위한 방법을 위해 다음과 같은 방법론들이 생겼다.

### Gradient Descent vs. Stochastic Gradient Descent

Batch 자체를 데이터 묶음이라고 하며, Batch Gradient Descent은 Batch 데이터를 기준으로 작성한다.

이 중, Stochastic Gradient Descent는 Batch 자체가 mini-batch 여러개로 나뉘어진 Batch 를 이용한다. mini-batch 하나가 완성될 때마다 업데이트 되는 형식으로 진행된다.

![https://t1.daumcdn.net/cfile/tistory/999EA83359D86B6B0B](https://t1.daumcdn.net/cfile/tistory/999EA83359D86B6B0B)

출처: [https://seamless.tistory.com/38](https://seamless.tistory.com/38)

Mini-Batch로 작동하는 것과 Batch 자체로 작동하는 건 큰 차이가 있다.

-   SGD: mini-batch는 완전히 일반적인 데이터가 아닌 한 쪽의 데이터를 이용하므로, 쉽게 일반화되지 않는다. 하지만 계산량이 적어서 유리하다.
-   GD: Batch를 기준으로 되므로, 덜 헤매다 찾겠지만, 계산량이 많은게 문제다.

다음 그림으로 쉽게 이해할 수 있다.

[##_Image|kage@B3QKy/btqUOBlIuuA/M4ecDJ4JkcO1jt2RuzBo60/img.png|alignCenter|data-origin-width="0" data-origin-height="0" width="358" height="NaN" data-ke-mobilestyle="widthContent"|||_##]

출처: [https://seamless.tistory.com/38](https://seamless.tistory.com/38)

### Additional: How to get theta?

수학 공식을 직접 이용해 theta를 구하려면, 다음과 같이 진행된다.

## Locally Weighted Linear Regression

### Underfitting and Overfitting

: 위 Linear Regression을 시도하면 할수록, 두 문제점 중 하나가 발생될 수 있습니다.

-   Underfitting: 모델이 데이터셋에 적합하지 않은 상황.
-   Overfitting: 모델이 과도하게 데이터셋에 적합한 상황. 일반 데이터셋이 나와도 일반화된 모델이 아니기에 적합하지 않다.

이러한 문제점들을 해결하기 위해, 구간에서만 한정적으로 적용되는 Locally Weighted Linear Regression을 제안한다. Linear Regression과 동일하게 적용되는데, Loss Function에서 구간에 관한 패널티를 적용해야 하므로 다음과 같이 정의된다.

![](https://render.githubusercontent.com/render/math?math=J(%7B%5Ctheta%7D)%20%3D%20%5Cfrac%7B1%7D%7B2%7D%5Csum_%7Bi%3D1%7D%5En%20w%5E%7B(i)%7D%7B(h_%7B%5Ctheta%7D(x%5E%7B(i)%7D)-y%5E%7B(i)%7D)%7D%5E%7B2%7D%20%5C%5Cw%5E%7B(i)%7D%20%3Dexp(-%5Cfrac%7B(x%5E%7B(i)%7D-x)%5E%7B2%7D%7D%7B2%5Ctau%5E2%7D))

구간에 대한 패널티는 다음과 같이 정의됩니다. tau(bandwidth 파라미터) 제곱을 더 나눠서 구간의 제약을 강화하게 됩니다. 패널티가 적용됨으로 인해 w 는 정규분포를 따르게 됩니다.

## Linear Regression의 보완ver. Logistic Regression

Linear Regression은 다음과 같이 나타나게 됩니다.

![](https://render.githubusercontent.com/render/math?math=h_%7B%5Ctheta%7D(x)%20%20%3D%20%7B%5Ctheta%7D%5ETX)

이러한 Regression은 특정 값을 가르키는데, 이 값을 이용해 \[0~1 사이로 매핑해 확률을 나타내는 문제들\]에 접근할 수 있습니다.

Logistic Function/Sigmoid Function을 이용해 매핑을 하게 됩니다.

![](https://render.githubusercontent.com/render/math?math=g(z)%20%3D%20%5Cfrac%20%7B1%7D%7B1%2Be%5E%7B-x%7D%7D)

위에 나온 **Linear Regression + Logistic Function ⇒ Logistic Regression**으로, 다음과 같은 공식으로 나타냅니다.

![](https://render.githubusercontent.com/render/math?math=h_%7B%5Ctheta%7D(x)%20%3D%20g(%7B%5Ctheta%7D%5ETx)%20%3D%20%5Cfrac%7B1%7D%7B1%2Be%5E%7B-%7B%5Ctheta%7D%5ETX%7D%7D)

밑 그림을 통해 둘의 차이를 확연히 볼 수 있습니다.

![https://static.javatpoint.com/tutorial/machine-learning/images/linear-regression-vs-logistic-regression.png](https://static.javatpoint.com/tutorial/machine-learning/images/linear-regression-vs-logistic-regression.png)

출처: [https://jinseob2kim.github.io/lecture-smc-psychiatry/regression/#1](https://jinseob2kim.github.io/lecture-smc-psychiatry/regression/#1)

이렇게 매핑된 값들은 다음과 같이 표현될 수 있습니다.

![](https://render.githubusercontent.com/render/math?math=%5Cbegin%7Bcases%7DP%5C%3B(y%3D1%20%5C%3B%7C%20%5C%3Bx%5C%3B%3B%5C%3B%7B%5Ctheta%7D%5C%3B)%20%26%20%3D%20h_%7B%5Ctheta%7D(x)%5C%5CP%5C%3B(y%3D0%20%5C%3B%7C%20%5C%3Bx%5C%3B%3B%5C%3B%7B%5Ctheta%7D%5C%3B)%20%26%3D%201-h_%7B%5Ctheta%7D(x)%5Cend%7Bcases%7D)

y=1일 확률을 h로 나타낸다면, 분류 문제에서는 1-h가 0이 될 확률로 매핑되며, 다음과 같이 정리됩니다.

![](https://render.githubusercontent.com/render/math?math=P%5C%3B(%5C%3By%5C%3B%7C%5C%3Bx%5C%3B%3B%5C%3B%7B%5Ctheta%7D%5C%3B)%20%3D%20%7Bh_%7B%5Ctheta%7D(x)%7D%5Ey(1-h_%7B%5Ctheta%7D(x))%5E%7B1-y%7D)

P에서 특정 x를 두고 정의한 Probability를 전체 X를 고려한 Likelihood 로 확장된다면 다음과 같이 나타날 수 있습니다.

![](https://render.githubusercontent.com/render/math?math=L(%7B%5Ctheta%7D)%20%3D%20P(%5C%3B%5Coverrightarrow%7B(y)%7D%5C%3B%7C%20%5C%3BX%5C%3B%3B%5C%3B%7B%5Ctheta%7D%5C%3B)%20%5C%5C%3D%20%5Cprod_%7Bi%3D1%7D%5En%20h_%7B%5Ctheta%7D(x%5E%7B(i)%7D)%5E%7By%5E%7B(i)%7D%7D(1-h_%7B%5Ctheta%7D(x%5E%7B(i)%7D))%5E%7B1-y%5E%7B(i)%7D%7D%5C%5C%20%5C%5C%0Al(%7B%5Ctheta%7D)%20%3D%20log(L(%7B%5Ctheta%7D))%20%3D%20%5Csum_%7Bi%3D1%7D%5En%20y%5E%7B(i)%7D%20log%20(h_%7B%5Ctheta%7D(x%5E%7B(i)%7D))%2B(1-y%5E%7B(i)%7D)%20log%20(1-h_%7B%5Ctheta%7D(x%5E%7B(i)%7D)))

다음과 같이 정리되어 결국 함수 l을 극대화하는 방향으로 작용됩니다.
