# axios에 대해서 


## axios에 알기 전에 알아야하는것


## 1. axios 4대장 

+ `GET` 서버에서 데이터를 받아옴 *데이터를 header에 포함*
+ `POST` : 서버로 데이터를 전송함
+ `PUT`: 수정 
+ `DELETE`: 삭제

## 2. await과 async에 대한 설명

axios는 비동기이다. `비동기`인 경우에는 작업이 완료되지 않은 상태에서 다른 코드가 실행될수 있다.

#### await과 async를 사용하는 이유는  비동기인 axios를 동기로 바꿔주는것이다.


+ ### async: async를 붙이면, 해당 함수는 항상 Promise를 반환

*특징 : async 함수 내에서만 await를 사용할 수 있다.*


+ ### await: 비동기 함수(Promise)가 처리될 때까지 기다린다.
즉, await가 붙은 비동기 함수는 실행이 끝날 때까지 그 다음 코드의 실행을 잠시 멈춘다.

       const response = await axios.get('https://api.example.com/data');


### awiat과 asyn에 대해서 간단설명: 기다렸다가 코드를 실행할수 있게 해주는것이다

+ content-type: 
+ post:
+ env

### 4. axios에 꼭 들어아갸하는것은 무엇일까?

+ try catch문
+ header문 *중요*
+ url



## 코드

```javascript
      try {               
        const response = await axios.get(
          `${process.env.NEXT_PUBLIC_REACT_APP_BASE_URL}/bed`,      //url이다
          { //이 {}이 꼭 필요하다.
            headers: {
              Authorization: `Bearer ${token}`,
              'ngrok-skip-browser-warning': '69420',  //ngrok을 사용할 때 나오는 경고 페이지를 우회하는 헤더
              withCredentials: true,  //쿠키 사용을 허락한다는것이다
            },
          }
        );
        setBedStatus(response.data);
      } catch (error) { //에러가 생겼을때 불러온다.
        console.error("침대 상태를 불러오는 중 에러 발생:", error);
      }

```


### 코드 설명



## axios에 대해서 간단설명

`try,catch`문이다
`header`이 필요하다.