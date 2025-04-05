# Reathook 

# 왜 이게 궁금해졌나

```javascript
const [email,setemail] = useState("");
```

이 코드를 보면서 왜 이코드를 사용하는지 궁금해졌다.


# Reacthook 에 대해서 

# useState

정의: useState

컴포넌트의 상태를 간편하게 생성하고 업데이트 해주는 도구를 제공해준다.

#### 불러오는 코드

```javascript
import { useState } from 'react';
```

이다. 
## useState 에 대해서 (니코)

useState는 항상 두개의 value 값을 return 한다


```javascript
const [item, setitem] = useState(1);
```

만약에 뒤에 setitem 이 필요가 없다면 

```javascript
const item=useState(1);
``` 
도 가능하다