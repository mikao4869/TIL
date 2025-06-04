# locall host https 변환하기

# 오류 개요
프로젝트를 배포했다. 하지만 수정해야하는 부분들이 있어서, 코드를 수정해야하는데, 배포를 한 상태에서는 코드 수정을 해도 변경사항이 안 변한다.

그럼 어떻게 해야할까?

백엔드: **localhost(http)를 https로 바꿔** 

근데 왜 ? 바꿔야하지?

    백엔드가 HTTPS이고 프론트엔드가 HTTP라서 서로 다른 origin으로 인식되어 요청이 차단되는 상황

아하 그러면 우선 오류에 대해서 하나하나 차근하게 알아볼까?

# 오류 

```typescript
Login:1 Access to XMLHttpRequest at 'https://api.gsm-dawa.com/auth/signin' from origin 'https://localhost:3000' has been blocked by CORS policy: Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource.이 오류 이해하기
requests.js:1 
           POST https://api.gsm-dawa.com/auth/signin net::ERR_FAILED
```

오류 해석

      요청 출처(origin): https://localhost:3000

      요청 대상: https://api.gsm-dawa.com/auth/signin

+ 나의 해석: `'https://localhost:3000'`로부터  'https://api.gsm-dawa.com/auth/signin'를 보냈는데 CORS 정책으로 인해 빠꾸먹음

+ GTP 해석: CORS(Cross-Origin Resource Sharing)**에 의해 API 요청을 차단했다는 뜻입니다.

**결론**: 아하 CORS 정책으로 인해서 바꾸먹었구나.! 
그러면 CORS정책이 뭐지???

## cors 오류

cors오류는?

**정의**: CORS (Cross-Origin Resource Sharing)는 웹 어플리케이션에서 다른 도메인의 리소스에 접근할 때 발생하는 보안 이슈를 해결하기 위한 표준 방법

즉 쉽게 말해서 **깐깐스러운 보안정책?**




cors 작동 방법


    1. 브라우저는 HTTP 요청을 보낸다.
    2. 서버는 요청에 대한 응답을 반환한다.
    3. 브라우저는 응답을 분석하여 CORS 헤더를 확인한다.
    4. CORS 헤더가 존재하면 브라우저는 자원에 대한 권한을 검사한다.
    5. 권한이 허용되면 자원을 사용하고, 그렇지 않으면 에러가 발생한다.




# 문제점을 해결방법


## localhost를 http --> https로 변환하기

