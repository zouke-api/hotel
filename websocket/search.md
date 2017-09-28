### 1. hotel.list

**描述**：检索酒店列表

**request**：
``` json
{
    "area":{"code":385130,"country":"意大利","name":"罗马","type":"zone"},
    "dateRange":{"in":"2017-09-13","out":"2017-09-14"},
    "currency":"EUR",
    "range":{"max":null,"min":null},
    "rooms":[
        {"roomNum":2,"adults":2,"children":0,"ages":[],"pid":1},
        {"roomNum":1,"adults":2,"children":2,"ages":[6, 15],"pid":2}
        {"roomNum":1,"adults":2,"children":2,"ages":[6, 6],"pid":3}
    ]
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

**说明**：请求中的area为选择区域时接口返回值，该结构必定会有`name`字段和`type`字段，其余字段可不关心，调用时直接把完整的结构传输给服务端，rooms字段，如果多房型中，存在人数和儿童年龄数相同房型，需要做合并，pid字段为数组索引默认从1开始。返回数据中finish字段标识该次推送是否是最后一次，注：如果不是最后一次，不会有finish字段！

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
    "cases": [
        {
            "board": {
                "breakfastFlag": 1,
                "cancelFlag": 1,
                "cancelInfo": [
                    {
                        "f_date": "2017-09-28",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 0,
                            "CNY": 0,
                            "EUR": 0,
                            "GBP": 0,
                            "HKD": 0,
                            "JPY": 0,
                            "NZD": 0,
                            "USD": 0
                        },
                        "t_date": "2017-11-14",
                        "t_time": "23:59"
                    },
                    {
                        "f_date": "2017-11-15",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 53,
                            "CNY": 275,
                            "EUR": 36,
                            "GBP": 31,
                            "HKD": 323,
                            "JPY": 4662,
                            "NZD": 58,
                            "USD": 42
                        },
                        "t_date": "2017-11-16",
                        "t_time": "23:59"
                    }
                ],
                "price": {
                    "AUD": 53,
                    "CNY": 275,
                    "EUR": 36,
                    "GBP": 31,
                    "HKD": 323,
                    "JPY": 4662,
                    "NZD": 58,
                    "USD": 42
                },
                "sessionObj": {
                    "currency": "EUR",
                    "hid": 374562,
                    "ratePlanId": "5:545985:34086945:2:1331:3:Y",
                    "searchParam": {
                        "area": {
                            "hotelId": 374562,
                            "type": "hotel"
                        },
                        "currency": "EUR",
                        "dateRange": {
                            "in": "2017-11-17",
                            "out": "2017-11-18"
                        },
                        "pid": 1,
                        "reqId": "15065635365329831171131554104034000904",
                        "rooms": [
                            {
                                "adults": 2,
                                "ages": [],
                                "children": 0
                            }
                        ]
                    },
                    "sid": "43315065635365329831171131554104034000904",
                    "sp": "dl",
                    "sp_id": 133504
                },
                "totalPrice": {
                    "AUD": 53,
                    "CNY": 275,
                    "EUR": 36,
                    "GBP": 31,
                    "HKD": 323,
                    "JPY": 4662,
                    "NZD": 58,
                    "USD": 42
                }
            },
            "hid": 374562,
            "room": [
                {
                    "desc": " ",
                    "name": "Double/twin",
                    "number": 1,
                    "person": 2
                }
            ],
            "sp": "dl",
            "sp_id": 133504
        },
        {
            "board": {
                "breakfastFlag": 1,
                "cancelFlag": 1,
                "cancelInfo": [
                    {
                        "f_date": "2017-09-28",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 0,
                            "CNY": 0,
                            "EUR": 0,
                            "GBP": 0,
                            "HKD": 0,
                            "JPY": 0,
                            "NZD": 0,
                            "USD": 0
                        },
                        "t_date": "2017-11-12",
                        "t_time": "23:59"
                    },
                    {
                        "f_date": "2017-11-13",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 54,
                            "CNY": 279,
                            "EUR": 36,
                            "GBP": 32,
                            "HKD": 328,
                            "JPY": 4729,
                            "NZD": 59,
                            "USD": 42
                        },
                        "t_date": "2017-11-16",
                        "t_time": "23:59"
                    }
                ],
                "price": {
                    "AUD": 54,
                    "CNY": 279,
                    "EUR": 36,
                    "GBP": 32,
                    "HKD": 328,
                    "JPY": 4729,
                    "NZD": 59,
                    "USD": 42
                },
                "sessionObj": {
                    "currency": "EUR",
                    "hid": 374562,
                    "ratePlanId": "25:46E627198687090D:BNN",
                    "searchParam": {
                        "area": {
                            "hotelId": 374562,
                            "type": "hotel"
                        },
                        "currency": "EUR",
                        "dateRange": {
                            "in": "2017-11-17",
                            "out": "2017-11-18"
                        },
                        "pid": 1,
                        "reqId": "15065635365329831171131554104034000904",
                        "rooms": [
                            {
                                "adults": 2,
                                "ages": [],
                                "children": 0
                            }
                        ]
                    },
                    "sid": "43315065635365329831171131554104034000904",
                    "sp": "dl",
                    "sp_id": 133504
                },
                "totalPrice": {
                    "AUD": 54,
                    "CNY": 279,
                    "EUR": 36,
                    "GBP": 32,
                    "HKD": 328,
                    "JPY": 4729,
                    "NZD": 59,
                    "USD": 42
                }
            },
            "hid": 374562,
            "room": [
                {
                    "desc": " ",
                    "name": "Twin/double Room",
                    "number": 1,
                    "person": 2
                }
            ],
            "sp": "dl",
            "sp_id": 133504
        },
        {
            "board": {
                "breakfastFlag": 1,
                "cancelFlag": 1,
                "cancelInfo": [
                    {
                        "f_date": "2017-09-28",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 0,
                            "CNY": 0,
                            "EUR": 0,
                            "GBP": 0,
                            "HKD": 0,
                            "JPY": 0,
                            "NZD": 0,
                            "USD": 0
                        },
                        "t_date": "2017-11-13",
                        "t_time": "23:59"
                    },
                    {
                        "f_date": "2017-11-14",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 54,
                            "CNY": 280,
                            "EUR": 36,
                            "GBP": 32,
                            "HKD": 329,
                            "JPY": 4746,
                            "NZD": 59,
                            "USD": 43
                        },
                        "t_date": "2017-11-16",
                        "t_time": "23:59"
                    }
                ],
                "price": {
                    "AUD": 54,
                    "CNY": 280,
                    "EUR": 36,
                    "GBP": 32,
                    "HKD": 329,
                    "JPY": 4746,
                    "NZD": 59,
                    "USD": 43
                },
                "sessionObj": {
                    "currency": "EUR",
                    "hid": 374562,
                    "ratePlanId": "1:118116:DBT-E10:ST:BB",
                    "searchParam": {
                        "area": {
                            "hotelId": 374562,
                            "type": "hotel"
                        },
                        "currency": "EUR",
                        "dateRange": {
                            "in": "2017-11-17",
                            "out": "2017-11-18"
                        },
                        "pid": 1,
                        "reqId": "15065635365329831171131554104034000904",
                        "rooms": [
                            {
                                "adults": 2,
                                "ages": [],
                                "children": 0
                            }
                        ]
                    },
                    "sid": "43315065635365329831171131554104034000904",
                    "sp": "dl",
                    "sp_id": 133504
                },
                "totalPrice": {
                    "AUD": 54,
                    "CNY": 280,
                    "EUR": 36,
                    "GBP": 32,
                    "HKD": 329,
                    "JPY": 4746,
                    "NZD": 59,
                    "USD": 43
                }
            },
            "hid": 374562,
            "room": [
                {
                    "desc": " ",
                    "name": "Double Or Twin Standard",
                    "number": 1,
                    "person": 2
                }
            ],
            "sp": "dl",
            "sp_id": 133504
        },
        {
            "board": {
                "breakfastFlag": 1,
                "cancelFlag": 1,
                "cancelInfo": [
                    {
                        "f_date": "2017-09-28",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 0,
                            "CNY": 0,
                            "EUR": 0,
                            "GBP": 0,
                            "HKD": 0,
                            "JPY": 0,
                            "NZD": 0,
                            "USD": 0
                        },
                        "t_date": "2017-11-13",
                        "t_time": "23:59"
                    },
                    {
                        "f_date": "2017-11-14",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 70,
                            "CNY": 364,
                            "EUR": 47,
                            "GBP": 41,
                            "HKD": 428,
                            "JPY": 6170,
                            "NZD": 76,
                            "USD": 55
                        },
                        "t_date": "2017-11-16",
                        "t_time": "23:59"
                    }
                ],
                "price": {
                    "AUD": 70,
                    "CNY": 364,
                    "EUR": 47,
                    "GBP": 41,
                    "HKD": 428,
                    "JPY": 6170,
                    "NZD": 76,
                    "USD": 55
                },
                "sessionObj": {
                    "currency": "EUR",
                    "hid": 374562,
                    "ratePlanId": "1:118116:TPL-E10:ST:BB",
                    "searchParam": {
                        "area": {
                            "hotelId": 374562,
                            "type": "hotel"
                        },
                        "currency": "EUR",
                        "dateRange": {
                            "in": "2017-11-17",
                            "out": "2017-11-18"
                        },
                        "pid": 1,
                        "reqId": "15065635365329831171131554104034000904",
                        "rooms": [
                            {
                                "adults": 2,
                                "ages": [],
                                "children": 0
                            }
                        ]
                    },
                    "sid": "43315065635365329831171131554104034000904",
                    "sp": "dl",
                    "sp_id": 133504
                },
                "totalPrice": {
                    "AUD": 70,
                    "CNY": 364,
                    "EUR": 47,
                    "GBP": 41,
                    "HKD": 428,
                    "JPY": 6170,
                    "NZD": 76,
                    "USD": 55
                }
            },
            "hid": 374562,
            "room": [
                {
                    "desc": " ",
                    "name": "Triple Standard",
                    "number": 1,
                    "person": 2
                }
            ],
            "sp": "dl",
            "sp_id": 133504
        },
        {
            "board": {
                "breakfastFlag": 1,
                "cancelFlag": 1,
                "cancelInfo": [
                    {
                        "f_date": "2017-09-28",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 0,
                            "CNY": 0,
                            "EUR": 0,
                            "GBP": 0,
                            "HKD": 0,
                            "JPY": 0,
                            "NZD": 0,
                            "USD": 0
                        },
                        "t_date": "2017-11-11",
                        "t_time": "23:59"
                    },
                    {
                        "f_date": "2017-11-12",
                        "f_time": "00:00",
                        "price": {
                            "AUD": 80,
                            "CNY": 415,
                            "EUR": 54,
                            "GBP": 47,
                            "HKD": 488,
                            "JPY": 7034,
                            "NZD": 87,
                            "USD": 63
                        },
                        "t_date": "2017-11-16",
                        "t_time": "23:59"
                    }
                ],
                "price": {
                    "AUD": 80,
                    "CNY": 415,
                    "EUR": 54,
                    "GBP": 47,
                    "HKD": 488,
                    "JPY": 7034,
                    "NZD": 87,
                    "USD": 63
                },
                "sessionObj": {
                    "currency": "EUR",
                    "hid": 374562,
                    "ratePlanId": "25:3B0160FE01B35CB7:BNN",
                    "searchParam": {
                        "area": {
                            "hotelId": 374562,
                            "type": "hotel"
                        },
                        "currency": "EUR",
                        "dateRange": {
                            "in": "2017-11-17",
                            "out": "2017-11-18"
                        },
                        "pid": 1,
                        "reqId": "15065635365329831171131554104034000904",
                        "rooms": [
                            {
                                "adults": 2,
                                "ages": [],
                                "children": 0
                            }
                        ]
                    },
                    "sid": "43315065635365329831171131554104034000904",
                    "sp": "dl",
                    "sp_id": 133504
                },
                "totalPrice": {
                    "AUD": 80,
                    "CNY": 415,
                    "EUR": 54,
                    "GBP": 47,
                    "HKD": 488,
                    "JPY": 7034,
                    "NZD": 87,
                    "USD": 63
                }
            },
            "hid": 374562,
            "room": [
                {
                    "desc": " ",
                    "name": "Triple Room",
                    "number": 1,
                    "person": 2
                }
            ],
            "sp": "dl",
            "sp_id": 133504
        }
    ],
    "pid": 1
}
```

**说明**：该接口请求参数与`查询酒店静态数据`接口中的请求参数一致

### 3. hotel.detail.nearby

**描述**：查询酒店的附近酒店

**request**: 同`hotel.detail.price`接口

**response**: 同`hotel.list`接口


