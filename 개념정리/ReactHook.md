# Reathook 

# 왜 이게 궁금해졌나

```javascript
const [email,setemail] = useState("");
```

이 코드를 보면서 왜 이코드를 사용하는지 궁금해졌다.


# Reacthook 에 대해서 
Hook은 함수형 컴포넌트에서 리액트의 기능들을 사용할 수 있도록 도와주는 특별한 함수입니다.


# useState

정의: 컴포넌트의 상태를 간편하게 생성하고 업데이트 해주는 도구를 제공해준다.

####   코드 

```javascript

import { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0); // count = 상태, setCount = 상태 바꾸는 함수

  return (
    <div>
      <p>현재 값: {count}</p>
      <button onClick={() => setCount(count + 1)}>증가</button>
    </div>
  );
}

```


#### 왜 사용하는것일까?   

긴 코드를 사용하므로 좀 더 효율적이게 코드를 사용하기 위해서랄까

#### 장점:   useState를 쓰면 리액트가 상태의 변경을 감지해서 자동으로 UI를 갱신해줍니다.

# 니코 설명

useState는 항상 두개의 value 값을 return 한다


```javascript
const [item, setitem] = useState(1);
```


# useEffect

정의: React에서 컴포넌트가 렌더링된 이후에 어떤 작업을 수행하고 싶을 때 사용하는 훅(Hook)입니다.

## 사용하는 경우

컴포넌트가 서버, 브라우저 API, 외부 라이브러리 등과 같은 외부 시스템과 통신하거나 동기화해야 할 때 useEffect가 필요하다. 예를 들어, 서버에서 데이터를 가져오거나, 외부 라이브러리의 위젯을 React 상태와 동기화하는 작업은 useEffect를 통해 처리할 수 있다.


### 규칙
두개의 인자가 필요하다. 하나는 `function`

만약 deps가 있다면 useEffect 리스트에 있는 값이있을때에만 변함


즉 try catch 문 같이 어떠한 조건이 있을땐 실행이 되고,
조건이 안되면 실행이 되지 않는거라고 생각하면 된다



#### [] 만약 아무것도 없으면? 

[] → 의존성 배열이 비어 있으므로 처음 마운트될 때 한 번만 실행

### 코드


```javascript
import { useEffect } from 'react';

useEffect(() => {
  // 실행할 코드
}, [의존성배열]);

```

