
### 1. /auth/is-login

**描述**：检测当前用户是否处于登录状态

**request**：
``` json
{ "token": "fdON29dizu-yowf44u7gpMLlxGnjnf4P" }
```

**response**：
``` json
{ "code": 0, "login": true, "uid": 10000 }
```

**说明**：请求token是当前用户身份标识，响应login表示token是否有效，无其它特殊code值。

### 2. /auth/login

**描述**：向服务端发起登录请求

**request**：
``` json
{
    "app": "hotel",
    "code": "071QhTOu1Mz1CxnT9VOu1xaYOu1QhTOg",
    "iv": "49wXK3kDJGEz3KrRxxcScQ==",
    "rawData": "{\"nickName\":\"name\",\"gender\":1,\"language\":\"zh_CN\",\"city\":\"ShangHai\",\"province\":\"ShangHai\",\"country\":\"China\",\"avatarUrl\":\"https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83eqDibmaujTj8U9mXgkj84wI1pLKBmMuZA4O1Wo4FONBUkLoP2fwG7oOQFhab8gPoDcITTjEricwNzzQ/0\"}",
    "signature": "349bea6fa554c98d991c5eaef7637498e546bf91",
    "encryptedData": "KUj8akmEhp7Zemb1mgvz6C9jqZBujilTbe8HF/9BAWhJuayBP5IRN9Cv08vmnMQGupG0PzicPANnIQEMDY+G5k65Nba/abHz2YkIWfLGH0+wBcXOJpe5mDdZqk4ggtZctls0ZOg9omEUzHXvCI4uJdRLbkJM45bR8+bAZMgKEAHH7OP69fxoh+aUuXM3h9epP8bTcPSRdCKWVftJmrq5Og10KHLI3PnM31aW1uX/S0Ea3cDnYbUz/VDyxgK6O5hKBB4Sgfw0QePfb8N/F9foL1v/gk3POTk1xZToiugyOFkXcQYVYmhHp1fxZ/aVHHAsSAcDWuvmCkCX8fWzFSf/KgXolhQJ4EnEJeQiliitpov2MfK2OwLdkWe3sL7s+4CLTWNZnmUIikthfwBjBh8U3VWao7W/TUfQ8VO5gUdMgrFfX+p5PzAdlFExUVXSkLPsz1XcO+u/tLpV9F+uZ215I0a3/bnR/xJYhB3pTkH4IE/AAS0B1QF/E5W/e1SACJbFG+s+cpLh/NNDjyuoiB9q0w=="
}
```

**response**：
``` json
{ "code": 0, "token": "XXXnvAJdSp52UJel7r0tW2cNVcIGhifL" }
```

**描述**： 请求app参数在该应用中固定为hotel，code参数是调用wx.login获取的code值，其余参数是调用wx.getUserInfo获取到的值(注：调用该小程序api时带上withCredentials)，响应token为当前用户身份标识，无其它特殊code值

**注**：除本接口外，其它http(s)接口都带token字段，其它接口中不再详细说明

### 3. /auth/get-user-info

**说明**: 获取用户详细信息

**request**：
``` json
{ "token": "fdON29dizu-yowf44u7gpMLlxGnjnf4P" }
```

**response**：
``` json
{
    "code":0,
    "info":{
        "id":260658,
        "nickName":"王克寒",
        "gender":1,
        "province":"浙江",
        "country":"中国",
        "city":"金华",
        "avatarUrl":"https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83erdhDveUv4KLMnrYCDHpHYazbqLIQEzu7SibobfNZzAUU3P2CODMiaHfoZ0rsBlfCZAqJrjGWpSVSyA/0",
        "identityPass":"pass",
        "tailorInfo":{"cover":"https://cdn1.zouke.com/tmp_c518a934bc31b700d270433e7cf504ca.jpg"},
        "card":{
            //以下是用户自已填写信息，在个人信息展示中优先显示以下信息
            "weix":"aaa",
            "company":"欧洲走客",
            "name":"王克寒",
            "brief":"个人简介",
            "email":"shjyh@qq.com",
            "phone":"18888888888",
            "avatar":"http://cdn1.zouke.com/journey/user/avatar/1483419156364_2084_ZW1haWxUZW1wbGF0ZTE0LmpwZw-guidepreview",
            "guide_area":"",
            "city":{    //所在地
                "code":387523,"name":"巴黎","gps":{"lat":48.856614,"lng":2.3522219000000177},
                "country_code":"FR","country_name":"法国"
            }
        }
    }
}
```

**描述**：响应info字段中的identityPass标识当前用户是否通过审核认证，只有审核通过才可以使用酒店预订功能

| identityPass | 描述 |
| ----- | ---- |
| 'pass' | 审核通过 |
| 'pending' | 审核中 |
| 'empty' | 无提交审核(新用户) |
| 'fail' | 审核不能过 |

### 4. /ht-app/user/get-ws-url

**说明**: 获取hotel websocket连接地址

**response**：
``` json
{
    "code": 0,
    "url": "wss://xxxx"
}
```


