---
layout: post
title:  데이터의 종류
date:   2019-11-16 09:00:00 +0900
categories: Note
---

#### 기본 데이터의 종류

Nominal Data / Categorical Data (명목자료)
- 남자/여자, 청팀/홍팀/백팀 등
 
Ordinal Data (순서자료)
- 좋다/그냥그렇다/나쁘다 등의 설문조사 데이터 등
 
Interval Data (구간자료)
- 시간 등
 
Ratio Data (비율자료)
- 나이, 돈, 몸무게 등

분류 기준 상세 
/images/note/data_type_1.jpg


데이터의 유형과 유형의 성격을 정확히 이해하는 것은 최초 데이터 수집 시 어떤 유형으로 데이터를 수집하는 게 적절할지 결정하는 일에서부터 이후 분석이나 시각화 과정에서 데이터 유형에 따라 할 수 있는/없는 일들이 결정되므로 중요하다.

1. nominal data (명목 자료)

nominal data는 nominal(이름과 관련한)이란 수식어에서 알 수 있듯이 여러 categories(예, 청팀, 백팀, 홍팀)들 중 하나의 이름에 데이터를 분류할 수 있을 때 사용된다.
nominal data는 순서를 매길 수 없고 그냥 셀 수 있을 따름이다.
평균을 계산하는 것이 의미 없고 (백팀과 홍팀의 평균은 연분홍팀?) percent로는 표현해도 된다. (청팀: 33%, 백팀 33%, 홍팀 34%)
특별히, nominal data가 두 개의 범주 중 하나에 속하는 경우 (남자 vs. 여자) dichotomous data(이분 자료)라고 부른다.
nominal data를 categorical data (범주형 자료)라 부르기도 한다.
2. ordinal data (순서 자료)

데이터가 속하는 category들에 순서가 있는 경우 ordinal data라고 한다. (순서가 있는 명목 자료)
예를 들면 청팀이 이길 가능성에 대해 survey를 하는 경우 그 답변을 “5. 매우 높다. 4. 높다. 3. 중립, 2. 낮다. 1. 매우 낮다."로 디자인할 수 있다.
nominal data와 마찬가지로 counting을 하고 percent로 표현해도 좋다. (매우 높다: 33%, 높다: 19%…)
단, 평균 (위 예에서 청팀 이길 확률에 대한 답변 평균이 3.8)에 대해서는 신중해야 한다. ordinal data에 대해 평균을 계산해서는 안 된다는 사람들이 있는데 이건 매우 높다에 5를, 높다에 4를 할당한 것처럼 그 각각의 (임의의) 숫자에 엄정한 수학적/과학적 의미가 있는 것이 아니기 때문이다. (하지만, 범주에 할당된 수와 순서별로 정렬된 범주에 할당된 수들의 차이값이 말이 되고 납득이 되는 경우 못 할 것도 없다. 신중만 하면 될 듯)
3. interval data (구간 자료)

시간을 ratio data(아래 참고)라고 보는 사람이 있는데 기본적으로 하루 중 특정 시점을 나타내는 시간은 interval data다.
데이터의 연속된 측정 구간 사이의 간격이 동일한 경우 interval data라고 부른다. (11:00와 11:05의 차이는 15:55과 16:00의 차이와 동일; 왜냐면, 매 분은 60초이니깐)
interval data는 numeric value를 가지므로 다양한 연산을 수행해도 된다.
단, 절대적 원점(zero point)이 없다. 무슨 말이냐면 00:00이라는 자료의 값이 측정한 시간의 값이 없다는 게 아니라 그냥 자정에 시간을 측정했다는 뜻.
4. ratio data (비율 자료)

현재 시각이 13:30인데 내가 시계를 보고 13:00부터 계산해서 “30분” 기다렸네 할 때 “30분"은 ratio data이다.
ratio data의 경우 interval data와 다르게 절대적 원점(meaningful zero point)이 존재하며 interval data에서 00:00이라는 값은 (기다린 시간이) “빵”초 라는 뜻이다.
나이, 돈, 몸무게 이런게 주로 ratio data로 다루어 진다.
5. discrete vs. continuous

interval이나 ratio 자료는 이산형(discrete)이나 연속형(continuous) 둘 중의 하나의 속성을 갖게 된다.
측정값이 정수로 딱딱 떨어지는 경우 이산형이고 연속된 무수히 많은 값 중 하나를 가질 수 있는 경우 연속형이 된다. 연속형 데이터는 실제 표현될 때 적당히 반올림 되어 표현된다.(몸무게: 72.5 kg) 현실에서 측정/이해하고자 하는 변수는 종종 하나 이상의 data type에 속하게 되며 변수의 data type은 어떤 측정(수집) 방법을 택하느냐에 따라 결정된다. 나이를 예로 들자면 나이(본질적으로 ratio data)는 ratio data로 수집될 수도 있지만 ordinal data로 수집될 수도 있다. (나이가 속한 그룹을 선택하는 방식으로 데이터를 수집한 경우, 21~25, 26~30, 31~35) 반면, nominal이나 ordinal data를 - 둘 다 category 유형 데이터 - interval이나 ratio data로 수집할 수는 없다. (청팀, 백팀, 홍팀으로 분류되는 데이터를 interval/ratio data로 수집할 수 없음) 보다 보편적으로 이야기하자면 데이터 측정은 주어진 데이터의 본질적 속성보다 더 성기고/낮은 수준으로 내려갈 (interval/ratio를 nominal/ordinal로 측정) 수 는 있어도 보다 더 정교한/높은 수준으로 올라갈 (nominal/ordinal을 interval/ratio로 측정) 수는 없다.
위에 이야기한 "내려갈 수는 있어도 올라갈 수 없다"는 법칙은 비단 데이터 수집뿐만 아니라 분석이나 시각화에도 적용된다. (예를 들어 ratio 유형으로 수집할 수 있는 데이터를 ordinal 유형으로 수집하게 되면 나중에 평균을 계산한다든지 기타 보다 정교한 분석을 수행하기 어렵고 표현할 수 있는 방식 역시 나이 그룹별 히스토그램 정도로 제한되게 된다.)