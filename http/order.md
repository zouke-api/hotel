### 1. /ht-app/order/commit

**描述**：提交订单

**request**：
``` json
{
    "contactTel": "18888888888",
    "invoice": {
        "need": true,
        "addr": "公司地址",
        "country": "other",
        "number": "税号",
        "title": "抬头",
        "weix": "联系微信"
    },
    "persons": [
        [ 
            {
                "first": "名",
                "last": "姓"
            }, 
            {
                "first": "名",
                "last": "姓"
            } 
        ]
    ]
}
```

**response**：
``` json
{
    "code": 0,
    "order_id": 100000
}
```

**说明**：请求参数sessionObj是酒店详情中价格列表结构中对应的sessionObj

### 2. /ht-app/order/get-order-info-to-pay

**描述**：获取用于支付的订单信息

**request**：
``` json
{
    "id": 10000 //订单号
}
```

**response**：
``` json
{
    "order":{
        "currency":"EUR",
        "price":{"CNY":1085,"EUR":142,"USD":170,"GBP":128,"HKD":1323,"AUD":212,"NZD":232,"JPY":18446},
        "listPrice":{"CNY":1085,"EUR":139,"USD":166,"GBP":125,"HKD":1297,"AUD":207,"NZD":227,"JPY":18084},
        "name":"Hotel Colosseum 圆形大剧场酒店",
        "roomCnt":1,
        "days":1,
        "checkInDate":"2017-09-14",
        "checkOutDate":"2017-09-15",
        "board":"含早",
        "contact":"bbb aaa",
        "roomInfo":[
            {
                "board":"含早",
                "name":"Double Or Twin Standard",
                "number":1,
                "price":{"CNY":1085,"EUR":139,"USD":166,"GBP":125,"HKD":1297,"AUD":207,"NZD":227,"JPY":18084},
                "adults":2,
                "children":0
            }
        ],
        "cancelFlag":false,
        "rate":{"AUD":5.264,"CAD":5.387,"CHF":6.825,"EUR":7.855,"GBP":8.718,"HKD":0.837,"JPY":0.06,"NZD":4.782,"SGD":4.872,"USD":6.543},
        "order_id":363567,
        "red_list":[]
    },
    "code": 0
}
```
**描述**：

| code | 说明 |
| --- | --- |
| 2 | 订单未找到(orderId错误) |
| 3 | 订单已关闭/删除 |

### 3. /ht-app/order/init-wx-payment

**描述**：初始化微信支付

**request**：
``` json
{
    "id": 10000,
    "red_id": 0         //红包id，如果没有，则为0
}
```

**response**：
``` json
{
    "id":362285,
    "jsApiParams":{
        "appId":"wx7uee0a346g3fd3z2e",
        "nonceStr":"g1th4uyte3tbts4d5w1l5jocahjxsix5okl5",
        "package":"prepay_id=",
        "signType":"MD5",
        "paySign":"67AF3E13931239AFD5EEDA80BADED63",
        "timestamp":"1505285004"
    },
    "code":0
}
```

**说明**：返回数据中jsApiParams用于调起微信开放接口中的支付功能

### 4. /ht-app/user/get-order-list

**描述**：获取订单列表

**response**：
``` json
{
    "code": 0,
    "list": [
        {
            "id":362674,
            "orderId":"H20170908362674",
            "htId":391503,
            "htName":"布拉格希尔顿酒店(Hilton Prague)",
            "checkInDate":"2017-10-01",
            "checkOutDate":"2017-10-03",
            "days":2,
            "roomNum":2,
            "board":"含早",
            "currency":"CNY",
            "price":{"CNY":34444,"EUR":4364,"USD":5154,"GBP":4014,"HKD":40380,"AUD":6512,"NZD":7133,"JPY":564656},
            "status":0,
            "statusDesc":"预订成功",
            "queryRooms":[
                {"adults":2,"ages":[],"children":0},
                {"adults":2,"ages":[],"children":0}
            ],
            "cancelFlag":true,
            "cancelInfo":[
                {
                    "price":{"CNY":0,"EUR":0,"USD":0,"GBP":0,"HKD":0,"AUD":0,"NZD":0,"JPY":0},
                    "f_date":"2017-09-08",
                    "f_time":"00:00",
                    "t_date":"2017-09-27",
                    "t_time":"23:59",
                    "range":"2017.09.08 00:00 - 2017.09.27 23:59"
                },
                {
                    "price":{"CNY":34444,"EUR":4364,"USD":5154,"GBP":4014,"HKD":40380,"AUD":6512,"NZD":7133,"JPY":564656},
                    "f_date":"2017-09-28",
                    "f_time":"00:00",
                    "t_date":"2017-09-30",
                    "t_time":"23:59",
                    "range":"2017.09.28 00:00 - 2017.09.30 23:59"
                }
            ],
            "cancelButton":true,
            "voucherStat":0,
            "voucherUrl":"/hotel/order/voucher-img?id=362674&r=621",
            "refNo":"DHB170908191107985",
            "hotelPhone":"+420224841111"
        }
    ]
}
```

**说明**：订单状态见下表

| status | 描述 |
| --- | --- |
| 0 | 预订成功 |
| 1 | 待支付 （订单提交后的状态）|
| 2 | 预定中 （订单付款后的状态） |
| 5 | 退款中 （用户申请退款后的状态） |
| 6 | 已退款 （退款完成后的状态） |
| 7 | 已关闭 （长期未支付，订单自动关闭） |
| 8 | 预定中 （系统预定失败，但客户端要显示预定中） |
| 9 | 已删除 （前端不会出现该状态）|

### 5. /ht-app/order/get-order-detail

**描述**：初始化微信支付

**request**：
``` json
{
    "id": 10000
}
```

**response**：
``` json
{
    "detail":{
        "id":362674,
        "price":{"CNY":34444,"EUR":4364,"USD":5154,"GBP":4014,"HKD":40380,"AUD":6512,"NZD":7133,"JPY":564656},
        "orderId":"H20170908362674",
        "hid":391503,
        "sp":"dl",
        "htName":"布拉格希尔顿酒店(Hilton Prague)",
        "checkInDate":"2017-10-01",
        "checkOutDate":"2017-10-03",
        "days":2,
        "contact":"YQ D，Hao G，HY S",
        "contactTel":"15618677060",
        "remark":false,
        "address":"Pobrezni 1, 布拉格, 18600, 捷克",
        "voucherStat":0,
        "voucherUrl":"/hotel/order/voucher-img?id=362674&r=958",
        "roomNum":2,
        "board":"含早",
        "cancelFlag":true,
        "cancelInfo":[
            {
                "price":{"CNY":0,"EUR":0,"USD":0,"GBP":0,"HKD":0,"AUD":0,"NZD":0,"JPY":0},
                "f_date":"2017-09-08",
                "f_time":"00:00",
                "t_date":"2017-09-27",
                "t_time":"23:59",
                "range":"2017.09.08 00:00 - 2017.09.27 23:59"
            },
            {
                "price":{"CNY":34444,"EUR":4364,"USD":5154,"GBP":4014,"HKD":40380,"AUD":6512,"NZD":7133,"JPY":564656},
                "f_date":"2017-09-28",
                "f_time":"00:00",
                "t_date":"2017-09-30",
                "t_time":"23:59",
                "range":"2017.09.28 00:00 - 2017.09.30 23:59"
            }
        ],
        "cancelButton":true,
        "status":0,
        "statusDesc":"预订成功",
        "rooms":[
            {
                "board":"含早",
                "name":"Presidential Suite",
                "number":2,
                "price":{"CNY":34444,"EUR":4364,"USD":5154,"GBP":4014,"HKD":40380,"AUD":6512,"NZD":7133,"JPY":564656},
                "adults":2,
                "children":0
            }
        ],
        "hotelPhone":"+420224841111",
        "email":null,
        "fax":null,
        "num":{"adults":4,"children":0},
        "supplements":[],
        "discounts":[],
        "allPerson":[
            {"first":"YQ","gender":1,"last":"D"},
            {"first":"Hao","gender":-1,"last":"G"},
            {"first":"HY","gender":-1,"last":"S"}
        ],
        "contacts":[
            [
                {"first":"YQ","gender":1,"last":"D"},
                {"first":"Hao","gender":-1,"last":"G"}
            ],
            [
                {"first":"HY","gender":-1,"last":"S"}
            ]
        ],
        "invoice":{"canModify":true,"need":false,"title":"","country":"","addr":"","weix":""},
        "queryRooms":[
            {"adults":2,"ages":[],"children":0},
            {"adults":2,"ages":[],"children":0}
        ],
        "refundedAmt":null,
        "currency":"CNY",
        "userId":3224171,
        "confirmNumber":"",
        "refNo":"DHB170908191107985"
    },
    "code":0
}
```

**说明**：订单状态status同上表

### 5. /ht-app/order/cancel

**描述**：取消订单

**request**：
``` json
{
    "id": 10000
}
```

**response**：
``` json
{
    "code":0
}
```