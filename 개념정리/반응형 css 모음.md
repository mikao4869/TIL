# 반응형 css 모음

## 개요

프로젝트 개발을 하면서 css부분이 걸렸다. 선배와의 노트북 화면크기로 인해 내가 지정한 css가 잘못된 위치로 보였기 때문이다.

나는 css를 `px`로만했기 때문에 이러한 문제가일어났다.

#### 그래서, gpt를 통해 알아본 경과 clamp함수를 알게 되어서 정리를 해보자


## clamp 사용법 및 개념 정리

```javascript
left: clamp(4vw, 7vw, 105px);
```

이렇게 보면 clamp 뒤에 3가지가있는데
`첫번째꺼: 최소값`
`두번째꺼: 선호값`
`세번째꺼: 최대값`

#### clamp(min, val, max)

이렇게 생각하면 편하다
즉 아까 내가 작성한 코드는 `4vw부터 105px`까지 사이즈가 조절된다는 말이다.

## em  

부모 요소를 기준으로  자식 요소의 크기를 정하는거

## rem

root을 기준으로 css 

## vh/vw

반응형을 만들때 가장 많이 사용하는거 

ex) F12 이 누르고 왔다리 갔다리 하면 화면 줄어드는거 확인할수있다.
`1vh = 10px ` 라고 생각하면서

`1vw = 10px`

## %
부모 요소 크기에 대한 상대적인 비율입니다. 부모 크기에 따라 유동적으로 크기가 변합니다.


# 미디어 쿼리
약간 if문으로 생각하면 된다.

ex) 
```javascript
@media (max-width: 768px) {
  /* 768px 이하(주로 태블릿, 모바일)에서 적용할 스타일 */
}

```

```javascript

/* 노트북 & 태블릿 가로 (해상도 1024px ~ 1279px)*/ 
@media all and (min-width:1024px) and (max-width:1279px) { 
  //스타일 설정
} 

/* 태블릿 가로 (해상도 768px ~ 1023px)*/ 
@media all and (min-width:768px) and (max-width:1023px) { 
  //스타일 설정
} 

/* 모바일 가로 & 태블릿 세로 (해상도 480px ~ 767px)*/ 
@media all and (min-width:480px) and (max-width:767px) {
  //스타일 설정
} 

/* 모바일 세로 (해상도 ~ 479px)*/ 
@media all and (max-width:479px) {
  //스타일 설정
}


```


