---
layout:     post
title:      "[번역] 캐글: 머신러닝 시작하기"
subtitle:   " \"Intro to Machine Learning\""
author:     "Jaeuk"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Translation
    - Kaggle
---

> 본 내용은 Kaggle [Intro to Machine Learning](https://www.kaggle.com/dansbecker/how-models-work) 을 참고하여 구성하였습니다.

우연히 유튜브에서 흥미로운 사람을 발견했습니다. Ken Jee 라는 유튜버인데, 데이터 사이언스에 관해 다양한 주제들로 영상을 제작하는 크리에이터 입니다. 이 분 영상 중  "[How I Would Learn Data Science (If I Had to Start Over)](https://www.youtube.com/watch?v=4OZip0cgOho)" 을 보면 데이터 사이언티스트를 준비하시는 분들에게 꽤나 도움이 될 것 같습니다. 다른 좋은 영상들도 많이 있으니 참고해보세요! Ken이 추천한 학습 방법 중 하나가 바로 제가 포스팅 할 **Kaggle micro-course** 입니다. Python부터 SQL, ML, DL 까지 상세하게 정리되어 있고, 무엇보다 실습이 있다는 것이 가장 큰 장점입니다.

## How Models Work

![First Decision Trees](http://i.imgur.com/7tsb5b1.png)

간단한 Decision Tree 모양입니다. 

이 Decision Tree는 오직 2개의 카테고리로 집들을 분류합니다. 예측된 가격은 같은 카테고리에 있는 집들의 평균 가격 정도로 이해하시면 됩니다.

사람들은 어떻게 집들을 두 개의 카테고리로 나눌 지 데이터를 사용해서 결정한 후, 각 그룹의 예측 가격을 결정합니다. 데이터로부터 이 패턴을 구성하는 단계를 **Fitting** or **Training** the model 이라 합니다. Model을 Fitting 시키는 데 사용되는 데이터를 **training data**라 합니다.

어떻게 모델이 Fitting 되는 지에 대한 내용은 꽤 복잡하기 때문에 나중에 심화 과정에서 배워도 됩니다. 모델이 한 번 Fitting 되고 나면 새로운 데이터를 사용해서 추가적으로 집 값을 예측할 수 있습니다.

#### Improving the Decision Tree

![First Decision Trees](http://i.imgur.com/prAjgku.png)

일반적으로 방이 2개 이상인 집이 더 비쌉니다. 따라서 왼쪽 Tree가 더 논리적으로 맞다는 것을 확인할 수 있습니다. 하지만 이것의 가장 큰 단점은 집들의 다양한 특징들을 고려하지 못한다는 것입니다...

![Depth 2 Tree](http://i.imgur.com/R3ywQsR.png)

따라서 tree를 보다 **Deep** 하게 구성해야 합니다. 이것도 사실은 부족하지만 이해를 돕기에는 충분하다고 생각합니다. 마지막으로 맨 끝에 위치한 박스? 를 **Leaf**라고 합니다.

## Basic Data Exploration

#### Using Pandas to Get Familiar With Your Data

```python
import pandas as pd
```

판다스 라이브러리 중 가장 중요한 것은 DataFrame 입니다. 데이터프레임은 데이터를 엑셀 표 처럼 구성해주는 역할을 합니다. 지금부터 Melbourne, Australia의 집값 데이터를 활용해서 pandas를 사용해보겠습니다.

```python
# save filepath to variable for easier access
melbourne_file_path = './data/melb_data.csv'
# read the data and store data in DataFrame titled melbourne_data
melbourne_data = pd.read_csv(melbourne_file_path) 
# print a summary of the data in Melbourne data
melbourne_data.describe()
```

