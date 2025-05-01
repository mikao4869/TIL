# Refresh Token 


# 개념

    Refresh Token은 Access Token을 재발급할 때 사용하는 키이다. 
    Access Token이 긴 만료 시간을 가지게 되면, 탈취당하여 악의적인 공격에 사용될 수 있다. 
    따라서 Access Token의 만료 기간을 짧게 유지하고, 상대적으로 긴 만료 시간을 가지는 Refresh Token을 통해 Access Token을 재발급 받음으로서 사용자가 로그아웃 없이 로그인 상태를 유지할 수 있게 한다.

로그인을 길게 해주게 해주는거!

![alt text](image-4.png)


# Access token


정의: 사용자가 로그인하면 발급받는 토큰입니다.


#### 특징
+ API 요청 시 “내가 인증된 사용자임”을 증명하기 위해 헤더에 실어서 보냅니다.

+ 유효기간이 짧습니다 (예: 1시간, 2시간 등).

+ 만료되면 더 이상 인증된 요청을 할 수 없습니다.

# refresh token

#### 특징

+ Access Token과 함께 발급받는 두 번째 토큰입니다.

+ 유효기간이 깁니다 (예: 2주, 한 달 등).

+ Access Token이 만료됐을 때, 이 Refresh Token을 서버에 보내면 새로운 Access Token을 재발급받을 수 있습니다.

+ Refresh Token이 만료되면 다시 로그인해야 합니다.

# 사용법


### 저장

```javascript
localStorage.setItem("accessToken", accessToken);
localStorage.setItem("accessTokenExpiry", (Date.now() + JWT_EXPIRY_TIME).toString());

```
accessToken은 localStorage에 저장되고,
 만료 시각(accessTokenExpiry)도 함께 저장됩니다.

### Refresh Token 

```javascript
localStorage.setItem("refreshToken", refreshToken);

```
### 자동 토큰 갱신

앱이 로드될때


```javascript
useEffect(() => {
    const refreshToken = localStorage.getItem("refreshToken");
    if (refreshToken) {
        onSilentRefresh();
    }
}, []);
```

### accessToken 만료시


```javascript
useEffect(() => {
    const expiry = localStorage.getItem("accessTokenExpiry");
    if (expiry && Date.now() > parseInt(expiry)) {
        onSilentRefresh();
    }
}, []);
```

accessToken이 만료된 경우에도 자동으로 갱신을 시도합니다.

### 갱신로직

```javascript
const onSilentRefresh = async () => {
    const refreshToken = localStorage.getItem("refreshToken");
    if (!refreshToken) {
        logout();
        return;
    }
    try {
        const response = await axios.post(
            `${process.env.NEXT_PUBLIC_REACT_APP_BASE_URL}/auth/reissue`,
            {},
            {
                headers: {
                    "Content-Type": "application/json",
                    "Refresh-Token": `Bearer ${refreshToken}`,
                },
                withCredentials: true,
            }
        );
        if (response.status === 200) {
            const { accessToken, refreshToken: newRefreshToken } = response.data;
            localStorage.setItem("accessToken", accessToken);
            localStorage.setItem("refreshToken", newRefreshToken);
            localStorage.setItem("accessTokenExpiry", (Date.now() + JWT_EXPIRY_TIME).toString());
            setTimeout(onSilentRefresh, JWT_EXPIRY_TIME - 60000);
        }
    } catch (error) {
        logout();
    }
};

```