## Summary
In this document we’re gonna show you how to make your HTTP API call to SenseCAP Hotspot Dashboard.

## HTTP HOST
- https://status.sensecapmx.cloud

## HTTP API Detail

**View Device Detail**

- Path: /api/openapi/device/view_device.
- Method: GET
- Parameters:
    - `api_key`: Apikey for your account.
    - `sn`: device sn.
- Access Control Quota: Up to 50 times per 5 minutes.
- Response

```
{
    "code": 0,
    "msg": "",
    "data": {
        "height": 1003444, // Block height of device
        "connected": 1,   // P2P Outbound Status. -1 unknown, 0：unhealthy, 1：healthy
        "dialable": 1,   //  P2P Inbound Status. -1：unknown, 0：unhealthy, 1：healthy
        "natType": 2,   //   -1：unknown, 0：none, 1：static, 2：symmetric, 3：restricted
        "ipPublic": [
            "113.110.229.80"
        ],
        "ipEthLocal": [
            "192.168.88.119"
        ],
        "ipWifiLocal": [
            "0.0.0.0"
        ],
        "syncList": [   //  History of block sync.
            {
                "height": 1003444, 
                "total": 1003457,
                "time": 1631180053960
            },
            ...(up to 10 rows.)
        ],
        "p2pAddress": [
            "/p2p/11LmGup58X4UXTajwmsYZhuXVcNYvnBCf4UGM3jx282iMotBR7j/p2p-circuit/p2p/112kS4A6sgZCTHU7gHyK1nBVhWVUMj2mSN11uARCEcREAd3WSj74"
        ],
        "fan_status_list": [   //  History of fan status.
            {
                "fan": 1,  // Fan status: 0-opened,1-closed.
                "temperature": 52, 
                "time": 1631181015278
            },
            ,
            ...(up to 5 rows.)
        ],
        "relay": false,
        "labels": [],
        "sn": "1109913212xxxxxxx",
        "address": "112kS4A6sg1CTHU7gHyK1nBVhWVUMj2mSN11uARCxxxxxxxx",
        "batch": null,
        "collectTime": 1631181103754, // Collect time of data.
        "cpuId": "100000002be60194",
        "cpuTemperature": 67,
        "cpuUsed": 37.6, // Percent of cpu used.
        "memoryTotal": 1900.79,
        "memoryUsed": 690.07,
        "name": "Fantastic Pecan Robin",
        "onboardingKey": "112kS4A6sg1CTHU7gHyK1nBVhWVUMj2mSN11uARCxxxxxxxx",
        "producedAt": 1625707693512,
        "region": "US915",
        "sdTotal": 58776.86,
        "sdUsed": 30533.79,
        "version": {
            "firmware": "2021.09.03.0"
        },
        "wifiSsid": "",
        "addToHeliumAt": 1624003515000,
        "gain": 1.2, // Gain of antenna.
        "owner": "xxxxxxxxxxxxxxxxxxxxxxxxxx",
        "geocode": {
            "short_street": "Irish-American Dam Rd",
            "short_state": "NV",
            "short_country": "US",
            "short_city": "Lovelock",
            "long_street": "Irish-American Dam Road",
            "long_state": "Nevada",
            "long_country": "United States",
            "long_city": "Lovelock",
            "city_id": "bG92ZWxvY2tuZXZhZGF1bml0ZWQgc3RhdGVz"
        },
        "heliumOnline": true,
        "lat": 40.21757423872224,
        "lng": -118.42763826806683,
        "totalHeight": 1003445, // Block height of helium.
        "synced": true,
        "online": true,
        "isHealth": 2, //  1：yes, 2：no,
        "relayed": 1  //  1：yes, 2：no,
    }
}
```

- example request

```
curl --request GET \
     --url https://status.sensecapmx.cloud/api/openapi/device/view_device?sn=<your device sn>&api_key=<your apiKey>
```

**Error Code**

| code | msg | description |
| :---: | :--- | :--- |
| 10000 | Framework analysis error | Service error. |
| 11100 | Invalid token | The apikey is Error. |
| 11200 | Request parameters are invalid | Request parameters are invalid. |
| 11203 | device no exists | This device is no exists. |
| 11207 | rate limit | The api is called too frequently. |
