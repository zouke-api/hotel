<style>
    table th:first-of-type{
        width:100px;
    }
</style>
所有接口以`JSON`作为数据交互

1. http(s)
  * 除登录接口外，其它接口都需要传token字段标识身份(可在登录接口获取token, 或在本地缓存token，当使用本地缓存token时，需要调用相应的接口校验token是否有效，详见[登录](http/login.md)部分)
  * 所有返回数据都会有一个code字段，如果为0，表示请求正确；如果<0，表示通用错误，如果>0，表示业务错误。（通用错误见下表）

    <table>
        <thead><tr>
            <th style="width:100px">code</th>
            <th>描述</th>
        </tr></thead>
        <tbody>
            <tr>
                <td>-1</td>
                <td>未登录</td>
            </tr>
            <tr>
                <td>-2</td>
                <td>数据校验错误</td>
            </tr>
        <tbody>
    </table>
  * 测试接口地址：http://tailor.wapp.test.zouke.com
  * **所有接口请求都需要带上以下http头**
    
    ``` yaml
    Content-Type: application/JSON; charset=UTF-8
    X-Requested_With: XMLHttpRequest
    ```

2. websocket
  * 协议格式

    ``` json
    {
        "event":"publish/subscribe",      //客户端发送消息使用subscribe/服务端推送消息使用publish
        "channel":"hotel.list",           //接口名称
        "mid":"1504667635712_1357",       //消息唯一id, 服务端在响应消息请求时会把该mid回传
        "data":{ "finish":true },         //传输数据
        "timestamp": 1504667679872        //时间戳
    }
    ```
  * websocket接口地址：ws://xxx?token=userToken
