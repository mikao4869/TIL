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


### useEffect

정의: 



## 사용하는 경우


컴포넌트가 서버, 브라우저 API, 외부 라이브러리 등과 같은 외부 시스템과 통신하거나 동기화해야 할 때 useEffect가 필요하다. 예를 들어, 서버에서 데이터를 가져오거나, 외부 라이브러리의 위젯을 React 상태와 동기화하는 작업은 useEffect를 통해 처리할 수 있다.