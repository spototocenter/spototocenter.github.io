---
layout: post
title:  Outlier and Imputation 
date:   2019-11-16 09:00:00 +0900
categories: Note
---

### Dataset I/O & 기본 정보 확인

파이썬 라이브러리인 Pandas를 통해 데이터를 읽고 내보낼 수 있습니다. <br> 
Pandas는 csv, html, xls 등 다양한 포멧을 지원합니다. <br>
Pandas는 DataFrame과 Series 2가지 형태의 데이터를 다룹니다. <br> 
Series는 DataFrame을 구성하는 하나의 열이라고 보면 되고, 여러 열이 하나의 DataFrame 구성합니다. <br> 
보통 한 Series에 속한 데이터 형태는 하나로 통일하는 것이 좋습니다.  

Pandas의 Set_index 메소드를 통해 index 지정 가능하고 head, info 및 describe 명령어를 통해 Dataset의 기본정보를 확인할 수 있습니다.

```python 
# read_csv를 이용해 dataset 불러오고 iduser를 index로 지정
df = pd.read_csv("mf.csv").set_index("iduser")
 
# 첫 행부터 5행까지 데이터 확인
df.head()
 
# rows 및 columns 개수, type, missing value 확인
df.info()
 
# 연속형 column에 한해, 기초 통계 확인 가능
df.describe()
```


### Continuous data outlier 

Box-Plot을 이용해서 이상치를 제거한다.<br>
여러 방법이 있지만, 사분위수를 이용해서 제거하는 방법을 사용한다.<br>
우선 Box-Plot은 4가지 구성요소가 있다.<br>

1) 중앙값(median): 말그대로 중앙값 50%의 위치이다.<br>
    중앙 값은 짝수일 경우 2개가 될 수도 있고, 그것의 평균이 중앙값이 될 수도 있다.<br>
    홀수일 경우, 중앙값은 1개가 된다.<br>

2) 박스(Box): 25%(Q1) ~75%(Q3) 까지 값들을 박스로 둘러 쌓는다.<br>
3) 수염 (whiskers): 박스의 각 모서리 (Q1, Q3)로 부터 IQR의 1.5배 내에 있는 가장 멀리 떨어진 데이터 점까지 이어져 있는 것이 수염이다.<br>
4) 이상치(Outlier): 수염(whiskers)보다 바깥쪽에 데이터가 존재한다면, 이것은 이상치로 분류 된다.<br>

Inter Quartile range (IQR) 이란?<br>
Q3 - Q1의 값이다.<br>

이상치를 구하기 위해서는 결국 수염을 이용하게 되는데, 이때 보통 1.5를 IQR에 곱한것으로 구한 수염을 이용한다.<br>

```python 
# use numpy 
np.percentile(x, 0)  # 최소값
np.percentile(x, 25)  # 1사분위 수
np.percentile(x, 50)  # 2사분위 수
np.percentile(x, 75)  # 3사분위 수
np.percentile(x, 100)  # 최대값

# use scipy 
from scipy.stats import describe
describe(x)

outlier = (Q1) - (1.5 * IQR), (3Q) + (1.5 * IQR) 
```

### boxplot 

```python 
# 패키지 불러오기

import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns
import numpy as np

# 화면 스타일 설정하기
sns.set_style("whitegrid")

# 파이썬에서 제공하는 데이터 불러오기
tips = sns.load_dataset("tips")

# 1. 상자그림 작성하기 : 가로 방향
sns.boxplot(x = "total_bill",  data = tips)
plt.show()

# 2. 상자그림 작성하기 : 세로 방향
sns.boxplot(x = "total_bill", orient = "v", data = tips)
plt.show()

# 3. 집단별 상자그림 작성하기 : 일변량 질적 자료
sns.boxplot(x = "day", y = "total_bill", data = tips)
plt.show()

# 4. 집단별 상자그림 작성하기 : 이변량 질적 자료
sns.boxplot(x = "day", y = "total_bill",  hue = "smoker", data = tips)
plt.show()

# 5. 집단별 상자그림 작성하기 : 색깔 변경하기
sns.boxplot(x = "day", y = "total_bill",  hue = "smoker", palette = "Set3", data = tips)
plt.show()

sns.boxplot(x = "day", y = "total_bill",  hue = "smoker", palette = "muted", data = tips)
plt.show()

sns.boxplot(x = "day", y = "total_bill",  hue = "smoker", palette = "RdBu", data = tips)
plt.show()

sns.boxplot(x = "day", y = "total_bill",  hue = "smoker", palette = "Blues_d", data = tips)
plt.show()

# 6. swarmplot 추가하기
sns.boxplot(x="day", y="total_bill", data=tips)
sns.swarmplot(x="day", y="total_bill", data=tips, color=".25")
plt.show()

# 7. factorplot 추가하기
sns.factorplot(x="sex", y="total_bill", hue="smoker", col="time", data=tips, kind="box", size=4, aspect=0.7)
plt.show()
```




