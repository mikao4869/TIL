# `e' 매개 변수에는 암시적으로 'any' 형식이 포함됩니다



# 문제의 코드
```javascript
    const handleEmail = (e) => {
        setEmail(e.target.value); // 오타 수정 및 타입 지정
      };
      
```

이렇게 하니, 오류가뜬것이다. 


# 원인및 해결법

#### 원인
typescript 같은 경우에는  type을 제대로 명시해야지, 잘 실행되는데

나같은 경우는 type을 잘 명시하지 않았기 때문에 오류가 생기는 것이다.

결론:typescript 같은 경우는  type의 명시를 잘해야한다.


#### 해결법: 
+ input 일때: `React.ChangeEvent<HTMLInputElement` 을 붙인다.
+ div 일때: `React.ChangeEvent<HTMLDivElement` 을 붙인다.


# 해결코드
```javascript
    const handleEmail = (e: React.ChangeEvent<HTMLInputElement>) => {
        setEmail(e.target.value); // 오타 수정 및 타입 지정
      };
```      