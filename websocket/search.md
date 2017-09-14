### 1. hotel.list

**描述**：检索酒店列表

**request**：
``` json
{
    "area":{"code":385130,"country":"意大利","name":"罗马","type":"zone"},
    "dateRange":{"in":"2017-09-13","out":"2017-09-14"},
    "currency":"EUR",
    "range":{"max":null,"min":null},
    "rooms":[{"roomNum":1,"adults":2,"children":0,"ages":[],"pid":"all"}]
}
```

**response**：
``` json
{
    "finish": true,
    "list":{
        "hotDesc":"罗马",
        "hotHotels":[],
        "hotels":[
            {
                "address":"Via Varrone 2/D, 普拉蒂 - 梵蒂冈城, 00193 罗马, 意大利",
                "address_en":"Via Varrone 2/D, Vatican City - Prati, 00193 Rome, Italy",
                "bk_url":"https://www.booking.com/hotel/it/deiconsoli.zh-cn.html",
                "booking_feature":"位置很赞！",
                "booking_feature_score":8.4,
                "booking_score":7.1,
                "check_in_time":"从14:00时",
                "check_out_time":"11:00时之前",
                "gps":{"lat":41.906386349807,"lng":12.459944486618},
                "hid":392326,
                "name":"Hotel dei Consoli 迪康索里酒店",
                "name_en":"Hotel dei Consoli",
                "name_zh":"迪康索里酒店",
                "phone":"+390668892972",
                "photo":"http://ht.cdn.zouke.com/bk/392326/1498753489127.jpg-w400",
                "position":"普拉蒂 - 梵蒂冈城,罗马,拉齐奥大区,意大利",
                "price":{"AUD":148.7,"CAD":144.9,"CHF":114.6,"CNY":782.5,"EUR":99.9,"GBP":90,"HKD":933.8,"JPY":13113.6,"NZD":163.7,"SGD":160.8,"USD":119.5},
                "services":{"board":false,"other":[],"stop":"停车场","tv":false,"wifi":true},
                "star":4,
                "tag":"四星级",
                "zone_name":""
            }
        ]
    }
}
```

**说明**：请求中的area为选择区域时接口返回值，该结构必定会有`name`字段和`type`字段，其余字段可不关心，调用时直接把完整的结构传输给服务端，rooms字段，如果多房型中，存在人数和儿童年龄数相同房型，需要做合并，pid字段固定为all。返回数据中finish字段标识该次推送是否是最后一次，注：如果不是最后一次，不会有finish字段！

### 2. hotel.detail.price

**描述**：检索酒店列表

**request**：
``` json
{
    "dateRange":{"in":"2017-09-13","out":"2017-09-14"},
    "currency":"EUR",
    "range":{"max":null,"min":null},
    "hid":392326,
    "rooms":[
        {"roomNum":1,"adults":2,"children":0,"ages":[],"pid":"all"}
    ]
}
```

**response**：
``` json
{
    "cases":[
        {
            "board":{
                "breakfastFlag":1,"cancelFlag":2,"name":"含早","price":{"AUD":159,"CNY":835,"EUR":107,"GBP":97,"HKD":996,"JPY":13911,"NZD":175,"USD":128},
                "sessionObj":{"xxx":"xxx"},
                "totalPrice":{"AUD":159,"CNY":835,"EUR":107,"GBP":97,"HKD":996,"JPY":13911,"NZD":175,"USD":128}
            },
            "hid":392326,
            "room":[
                {"desc":"","name":"双人间","number":1,"person":2}
            ],
            "sp":"vt",
            "sp_id":15954
        },
        {
            "board":{
                "breakfastFlag":1,"cancelFlag":2,"name":"含早","price":{"AUD":184,"CNY":964,"EUR":124,"GBP":111,"HKD":1151,"JPY":16067,"NZD":202,"USD":148},
                "sessionObj":{"xxx":"xxx"},
                "totalPrice":{"AUD":184,"CNY":964,"EUR":124,"GBP":111,"HKD":1151,"JPY":16067,"NZD":202,"USD":148}
            },
            "hid":392326,
            "room":[
                {"desc":"","name":"双床 双人间","number":1,"person":2}
            ],
            "sp":"vt",
            "sp_id":15954
        }
    ]
}
```

**说明**：该接口请求参数与`查询酒店静态数据`接口中的请求参数一致

### 3. hotel.detail.nearby

**描述**：查询酒店的附近酒店

**request**: 同`hotel.detail.price`接口

**response**: 同`hotel.list`接口


