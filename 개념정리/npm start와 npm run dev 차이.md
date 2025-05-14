# npm start와 npm run dev의 차이

어떨때는 npm start , 어떨때는 npm run dev 헷갈린다.

약간 쉽게 말하자면

## 기억하자

#### react --> `npm start`

#### next js --> `npm run dev`


## 근데 왜?

#### `npm start `  --> 

**create-react-app으로 만든 프로젝트**는 npm start를 개발 명령어로 쓰도록 기본 설정


### `next js ` -->

Next.js는 **개발 서버 명령어가 dev**로 정의되어 있어요.


## package.json 설정


만약 package.json에 이러한 설정을 했으면 
```javascript

  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  }
```
지금 이 코드는 next js가 있을때의 코드이다.


    그냥 아무것도 설정안했으면 `npm start`

+ next dev ⇒ 개발 모드에서 실행
+ next build ⇒ 프로덕션 빌드 용도로 애플리케이션 빌드
+ next start ⇒ Next.js 프로덕션 서버 시작


## next js가 바라보는 명령어들

![alt text](../개념정리/이미지/next%20js%20명령어%20차이점.png)

## 질문

#### next js를 사용하는데 npm start를 사용해도 될까?


위의 그림을 보는것처럼 next js에서 npm start를 하는것은 빌드된 앱을 실행하는것으로 

**하면 안되는 이유**
1. `npm run build` 이후에 npm start를 해야한다.
2. 수정해도 화면에 반영 안 됨 → Hot Reload가 없음
3. 느리고 번거롭다
→ 수정할 때마다 빌드 다시 해야 함


이러한 이유로 **next js를 사용하고 있는데, npm start를 사용하면 안되는 이유이다.**


# 결론 : 

### Next js : `npm run dev` !
### React:  `npm start`



## 그럼 똑같은 next js에서의

`npm run dev와`

`npm run build`와
`npm run start`는 뭘까?


하나하나씩 설명을 하자면


#### npm run dev : 개발모드로 실행
#### npm run build : 개발이 끝난후 배포를 하기 위해서 하는 명령어  
--> 코드 압축,  
#### npm run start : 배포를끝난후 서비스를 시작하는 명령어

--> build를 한다음에한다.


![이](이미지/nextjs%20명령어%20차이.png)