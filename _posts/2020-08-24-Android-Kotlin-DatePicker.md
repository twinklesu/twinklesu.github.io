---
layout: post
comments: true
title: "Andorid Kotlin DatePicker 만들기"
date: 2020-08-24 01:53:30
permalink: '/android'
---

# 안드로이드 캘린더에서 날짜 고르는 

버튼을 누르면 캘린더가 떠서 날짜를 고르고, 시계가 떠서 시간을 고르는 기능! 

![image](https://user-images.githubusercontent.com/68603692/90983080-77796e00-e5a6-11ea-9efe-6c95fbf5122b.png)

바로 요녀석!! 바로 만들어 보겠다.

Manifest와 gradle에 추가는 없다


## activity_main.xml
<script src="https://gist.github.com/twinklesu/1cdd5925b0f7f7434e9f3f593b592421.js"></script>


날짜를 입력하는 버튼과 선택된 날짜를 보여주는 textview를 만들었다. 

![image](https://user-images.githubusercontent.com/68603692/90983235-91678080-e5a7-11ea-99ce-9cdc87cdec08.png)

(이건 다음 글에 쓸 TimePicker도 함께 있는 UI다.)


## MainActivity.kt
<script src="https://gist.github.com/twinklesu/9f2d7dfebd0d3a499d591bec6feb45b8.js"></script>

일단 `val cal = Calendar.getInstance()`을 class내에서 쓰일 수 있도록 앞부분에 선언해 준다. 
`onCreate()` 함수 안에서는 버튼(`btn_date`)을 누르면, `showDatePicker()`가 실행 되도록 했다. 연습할 때는 버튼의 `setOnClickListener`에서 바로 실행내용을 적어도 되겠지만, 여러 사람과 함께 만드는 어플이라 가독성을 위해 따로 했다. 그리고 따로 하면 나중에 코드 복붙하기도 쉬우니까..!

---
`showDatePicker()` 함수를 살펴보자. `->`가 있는걸 보면 람다식인 것 같은데..(람다식 코틀린 처음 공부할 때 읽어보긴 했는데 이해는 못했다^^ 나중에 하겠지~) 
앞에서부터 차근차근 생각을 해보자.
`DatePickerDialog` 함수 안에 `DatePickerDialog.OnDateSetListener` 함수가 들어있는 형태로 생각하자. 
1. `DatePickerDialog`는 맨 끝의 `.show()`로 인해 화면에 띄워진다. dialog라는 것들이 안드로이드에서 액티비티(화면) 위에 띄워지는 아이들을 다 다이얼로그라고 하는 것 같다.
2. 리스너의 `->` 이후 줄엔 다이얼로그에서 선택된 날짜로 실행할 코드를 적어준다. 나는 `tv_date`라는 텍스트뷰에 작성해줬다.
3. 주의할 점은 `month` 값이 0부터 시작하기 때문에 1을 더해서 출력에 사용해야한다. (우리나라의 월이 숫자를 써서 다행이다. JAN, FEB등으로 바꿀 생각하면...어후...)
---
다이얼로그를 띄웠을 때 보여질 기본 날짜 세팅은 현재 기기의 날짜와 일치한다. 이를 변경하고 싶다면, 

`cal.set(Integer.parseInt(year), Integer.parseInt(month)-1, Integer.parseInt(date))`

를 cal 선언 이후에, dialog전에 설정해주면 된다. 이 경우 나는 year, month, date를 String으로 해둬서 `parseInt`를 사용했다. 


## 꼼지락
다음 글에서는 세트로 쓰는 TimePicker()를 만들어 보겠다. TimePicker는 24시간제 때문에 설정할게 많았다...
사실 EditText로 만들어서 하고싶었는데 그럼 키보드가 켜져서 너무 부자연스러웠다ㅜㅜ 가끔 인터넷 쇼핑몰 어플을 이용할 때면 어플이 쓰레기같단 생각을 가끔하는데... 쿠* *팡 같은 곳의 어플보다 질이 떨어지니까...? 근데 그것도 너무 정성가득한 어플임을 뼈저리게 느낀다. 
너무 내 설명이 부족하고 깊이감이 없는 것 같지만 ㅜㅜ 사실 과제하면서 구글링해보면 설명 하나도 안 읽고 코드만 보니까 ㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋ 필요한것만 적어보기... 
