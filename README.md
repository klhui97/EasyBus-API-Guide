## EasyBus-API-Guide

## 簡介
EasyBus只提供搜尋巴士及瀏覽到站時間的介面，EasyBus並不提供到站時間服務，開發者可以跟隨以下教學建立一個API endpoint給用家使用到站時間服務

## EasyBus HTTP/HTTPS request
#### Method
```
Get
```
#### Parameter
| Key | Value / Type | Notes |
|-----|-------|---|
|action|"geteta"|specify action|
|lang|"tc"|language| 
|route|String|Bus number|
|stop_seq|String|Stop number|
|servicetype|String|Service type|
|bound|String|Bound|
|stop|String|Stop bsicode|

#### GET example on Postman
Our app sends GET request. You can define your response by getting the parameters that we send.
```
GET http://example.com/?action=geteta&route=1&stop_seq=16&servicetype=1&bound=1&lang=tc&stop=NA06S17500
```

## Define a response
A json response is required. An array with the key "response" is required. The "response" contains N eta dictonary. This dictonary must contain the below information:

| Key | Value | Type | Notes |
|-----|-------|---|---|
|w|"Y" / "N"|String(Optional)|to indicate if the bus is operating|
|ex|"2018-1-1 20:15:18"|String|exact arrival time, will be displayed directly|
|t|23:10  預定班次|String|23:10 will be used to calculate the remaining time, the string after "  " will be displayed directly|

#### Response example 1
```
{
    "response": [
        {
            "w": "Y",
            "ex": "2018-1-1 20:15:18",
            "t": "23:10  預定班次"
        }
    ]
}
```
#### Response example 2
```
{
    "response": [
        {
            "w": "Y",
            "ex": "2018-1-1 20:15:18",
            "t": "23:10"
        }
    ]
}
```

## Done
You can test your api in our app -> Setting -> About EasyBus -> paste your link -> Confrim and test.
Our app will tell you if your api is compatible to our app.
