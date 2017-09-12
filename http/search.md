### 1. /hotel/query/get-recommend-list

**描述**：获取当前用户的历史查询和热门城市

**request**：
``` json
{ "token": "fdON29dizu-yowf44u7gpMLlxGnjnf4P" }
```

**response**：
``` json
{
    "history":[
        { 
            "id":364410,
            "params":{
                "area":{"code":385130,"country":"意大利","name":"罗马","type":"zone"},
                "currency":"EUR",
                "dateRange":{"in":"2017-09-07","out":"2017-09-08"},
                "range":{"max":null,"min":null},
                "rooms":[{"adults":2,"ages":null,"children":0,"pid":"all","roomNum":1}]
            }
        }
    ],
    "hot":[
        {"code":387523,"name":"巴黎","country":"法国","type":"zone"},
        {"code":3140971,"name":"因特拉肯","country":"瑞士","type":"zone"},
        {"code":390333,"name":"捷克克鲁姆洛夫","country":"捷克","type":"zone"}
    ],
    "code":0
}
```

**说明**：响应hot字段表示热门城市，history字段表示查询历史，查询历史每一项都是一个完整的检索条件，完整的检索数据结构详见websocket模块

### 2. /hotel/query/delete-query-history

**描述**：删除历史查询

**request**：
``` json
{ "token": "fdON29dizu-yowf44u7gpMLlxGnjnf4P", "id": 364410 }
```

**response**：
``` json
{
    "history":[
        { 
            "id":364410,
            "params":{
                "area":{"code":385130,"country":"意大利","name":"罗马","type":"zone"},
                "currency":"EUR",
                "dateRange":{"in":"2017-09-07","out":"2017-09-08"},
                "range":{"max":null,"min":null},
                "rooms":[{"adults":2,"ages":null,"children":0,"pid":"all","roomNum":1}]
            }
        }
    ],
    "code":0
}
```

**说明**：请求id字段标识历史记录id，响应history字段表示删除一条后新的历史记录

### 2. /hotel/query/search-word

**描述**：根据关键字查询 城市/地标/酒店名

**request**：
``` json
{ "token": "fdON29dizu-yowf44u7gpMLlxGnjnf4P", "word": "d" }
```

**response**：
``` json
{
    "list":[
        {"area":{"code":3101065,"name":"Dahn","country":"Palatinate Forest,Rhineland-Palatinate,Germany","type":"zone"}},
        {"area":{"code":391056,"name":"Dadia","country":"Thrace,Greece","type":"zone"}},
        {"area":{"code":64053,"name":"D-Day Museum","country":"朴次茅斯,英国","gps":{"lng":-1.089412,"lat":50.77964},"type":"poi"}}
    ],
    "code":0
}
```

**注**：实时查询时，不要过于频繁调用该接口，前端可以使用debounce防抖方法

### 3. /hotel/query/get-hotel-static-data

**描述**：获取酒店的静态数据

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
    "detail":{
        "hid":392326,
        "name_zh":"迪康索里酒店",
        "name_en":"Hotel dei Consoli",
        "address":"Via Varrone 2/D, 普拉蒂 - 梵蒂冈城, 00193 罗马, 意大利",
        "booking_feature":"位置很赞！",
        "booking_score":7.1,
        "booking_url":"https://m.booking.com/hotel/it/deiconsoli.zh-cn.html?label=sid%3D4;sid=1;checkin=2017-09-13;checkout=2017-09-14;no_rooms=1;req_adults=2;selected_currency=EUR;changed_currency=1;top_currency=1;",
        "desc":"这家酒店距离梵蒂冈仅有400米，酒店屋顶的露台可以尽览整个圣彼得大教堂。客房提供免费无线网络连接，拥有典雅的粉刷墙面装饰，配有地毯和挂毯。\n\nHotel dei Consoli酒店的客房都配备了空调、电视和迷你吧，并设有现代化的浴室。部分客房配有Jacuzzi®水疗浴缸或水力按摩淋浴。\n\n露台上种有柑橘树和橄榄树，并设有带意大利手工装饰陶瓷的咖啡厅。晚餐时，酒店提供意大利经典美食和素食这2种不同的菜单供客人选择。早餐时，酒店可应要求提供无麸质菜单。\n\nDei Consoli酒店的前台每天24小时开放，并可以安排幼儿看护和机场班车服务。酒店距离梵蒂冈地铁站有5分钟的步行路程。\n\n旅友们喜爱普拉蒂 - 梵蒂冈城的理由：博物馆、艺术和文化。\n\n\n夫妻/情侣特别喜欢这家住宿的位置，为两人住宿体验给出了8.5分。",
        "gps":{"lng":12.459944486618,"lat":41.906386349807},
        "photos":[
            "http://ht.cdn.zouke.com/bk/392326/1498969349892.jpg-w800","http://ht.cdn.zouke.com/bk/392326/1498969349504.jpg-w800","http://ht.cdn.zouke.com/bk/392326/1498969349402.jpg-w800","http://ht.cdn.zouke.com/bk/392326/1498969349284.jpg-w800",
        ],
        "services":{
            "facilities":[
                {"code":13,"name":"户外","items":["露台"]},
                {"code":-2,"name":"宠物","items":["不允许携带宠物入住。"],},
                {"code":2,"name":"活动设施","items":["自行车租赁（额外收费）"]},
                {"code":7,"name":"餐饮服务","items":["特别节食菜单（应要求提供）","小吃吧","在客房内享用早餐","酒吧"]}
            ],
            "hotFacilities":["免费无线网络连接","停车场","机场班车","禁烟客房","无障碍设施","客房服务"]
        },
        "star":4,
        "tag":"四星级",
        "check_in_time":"从14:00时",
        "check_out_time":"11:00时之前"
    },
    "code":0
}
```

**注**：该接口请求参数与`websocket`中查询报价接口的请求参数一致