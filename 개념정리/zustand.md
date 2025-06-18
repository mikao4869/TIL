# zustand

## zustand가 뭐지??

상태를 뜻한다.
단순화된 Flux 원리를 사용하는 작고 빠르며 확장 가능한 상태 관리 솔루션이다. Hooks에 기반해 편리한 API를 제공한다.

서현정의 : 상태관리하기 위해서 쉬운 tool 


## 장점
+ 쉽다 간단하다


## 사용법

설치 


```ts
npm install zustand
```


store 상태 정의 
```TS
// src/store/useCounterStore.ts
import { create } from 'zustand';

interface CounterState {
  count: number;
  increase: () => void;
  decrease: () => void;
}

export const useCounterStore = create<CounterState>((set) => ({
  count: 0,
  increase: () => set((state) => ({ count: state.count + 1 })),
  decrease: () => set((state) => ({ count: state.count - 1 })),
}));
```


컴포넌트 사용
```ts
// Counter.tsx
import { useCounterStore } from '../store/useCounterStore';

function Counter() {
  const { count, increase, decrease } = useCounterStore();

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increase}>+</button>
      <button onClick={decrease}>-</button>
    </div>
  );
}

export default Counter;
```