---
layout: post
comments: true
title: "Android Kotlin TimePicker 만들기"
date: 2020-08-25 16:20:30
permalink: '/android'
---

# 안드로이드 시계에서 시간 입력하기

버튼을 누르면 시계가 뜨고, 시간을 입력하는 다이얼로그를 만들어 보쟈!

![image](https://user-images.githubusercontent.com/68603692/91141347-d942f080-e6ea-11ea-9142-12fe7a985441.png)

요녀석! 이전 게시글인 DatePicker 와 마찬가지로 Manifest 와 Gradle에 추가 사항은 없다.

## activity_main.xml

<script src="https://gist.github.com/twinklesu/e18cadbe558e3707bcae7fc85f6d4333.js"></script>

그냥~ 버튼 하나와 입력된 시간을 보여줄 텍뷰를 하나 만들어 준다

![image](https://user-images.githubusercontent.com/68603692/91142175-4f475780-e6eb-11ea-99c5-b317b3670025.png)

이건 DatePicker도 함께 있지만 대강 이런식!

## MainActivity.kt

<script src="https://gist.github.com/twinklesu/51c71bf0d2afa2bd63310ab0390fe945.js"></script>

1. class 내부에 `val cal = Calendar.getInstance()`로 캘린더를 선언해준다.
2. 버튼을 누르면 DatePicker() 함수가 실행 된다.
3. `show()` 이전의 파라미터 중 `false`는 24시간제를 이용할지, 12시간제를 이용할지에 해당되는 변수이다. 
	`false`를 고르면 맨 위의 사진과 같이 오전 오후를 고르게 되고, `true`일 경우, 
	![image](https://user-images.githubusercontent.com/68603692/91143070-e52fb200-e6ec-11ea-84ba-5703451ed1ee.png)
	이렇게 요상한,,, 시계를 사용하게 된다. 
4. 다이얼로그 내부 코드는 DatePicker 게시글을 보거나 그냥 읽어보면 이해가 될텐데, 나의 경우 시간을 그냥 띄워주는게 아니라 오전, 오후 를 한글로 보여주고 12시간제로 나타내고 싶었다. 이게.. true, false로 24시간제 12시간제를 골라도, 받아지는 값은 동일하게 24시간제로 **00~24**의 Int가 hr의 값으로 받아진다. 
5. `"%02d".foramt(min)`의 경우 5분이라면 05분 으로 뜨길 바라면서 포멧팅을 해준 것이다. 대강 0이 2개 들어가는 decimal 이라고 외우면 될 것 같다! 

## 시간 프리셋 하기
<script src="https://gist.github.com/twinklesu/e91a2d7c9e9b1c404149691c8e43fc9a.js"></script>

시계 다이얼로그를 정해진 시간으로 띄우고 싶어 활용한 코드다.
이전의 피커 함수에서 변수 두가지를 추가해줬는데, 
1.  두개의 TimePicker를 한 액티비티 안에서 필요로 해서 `btn`변수를 넘겨줬다. 이전에서는 입력된 시간을 텍뷰에 띄웠지만 여기선 버튼에 띄웠다.
2. `time`의 경우 프리셋 하고 싶은 시간을 String 형태인 **"13:05"**와 같은 형태로 넘겼다. 
중요한 것은 `time`인데, `time` 변수가 있다면 
`cal.set(Calendar.HOUR, Integer.parseInt(time.substring(0,2)))` 
으로 프리셋 해줬다. 
`time` 변수가 없을 땐 그냥 기기의 현재시간으로 자동 설정된다.

## 꼼지락

아 몬가 내가 사람들 블로그 여기저기에서 찾아 읽고 활용할 때는 블로그에 정리하고 싶은 마음이 컸는데 막상 하려니까 진짜 귀찮고 재미가 없다...ㅜㅜ 그냥 이런거는 안하구, 백준 알고리즘 같은거 푸는 것만 정리해서 올려야하나.. 다른 블로그들꺼 요약 짜집기라는 생각에 너무 현타가 온다. 하지만 코드 원래 다 구글링해서 짜는거잖아요..? 그리고 그냥 네이버 블로그나 할걸 뭐한다고 깃헙 블로그를 시작해서 사진 하나 올리는데도 깃헙 이슈 열어서 하구~ 그래야하나 싶다... 너무 귀찮은데 흑흑
아직도 블로그의 카테고리 기능을 완성하지 못했다 ㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋ 오늘은 할 수 있을까.. 너무 귀찮다 허허 
