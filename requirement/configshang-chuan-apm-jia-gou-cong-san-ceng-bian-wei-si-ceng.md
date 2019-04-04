# Config上傳APM架構從三層變為四層

---

### 目標

* 考量一個EdgeX可能同時有多個gateway, 每個gateway都要配置一次WISE-PaaS連線資訊的話會造成使用者困擾, 所以改為一個EdgeX只要配置一次

### 修改幅度

* edgex-ui-go

  * UI
    * WISE-PaaS Setting - WhiteList
      * 增加Gateway下拉選單, 先選擇gateway, 再選擇該gateway下的device, 再列出該device下的value desciptor
  * API

    * /wisepaas/setting/{gatewayId} 改成 /wisepaas/setting

    * 產生APM config部分

      * 修改上傳APM的config format

      ```
      {
        "edgeSource": "edgeXSource",
        "command": 101,
        "ts": 123456,
        "profileInfo": {
          "profileName": "xx",
          "description": "this is an example model",
          "gateways": [
            {
              "gatewayId": "xxx",
              "gatewayName": "xxx",
              "iotSense": {
                "type": "EdgeX",
                "groupId": "APMId",  // EdgeX填写APM ID
                "groupName": "groupName"
              },
              "devices": [
                {
                  "deviceId": "Scada/RMM deviceId",
                  "deviceName": "exampleDeviceName(RMM: AgentName/Scada: deviceName)",
                  "deviceProfileName": "xx",
                  "tags": [
                    {
                      "name": "temp",
                      "tag": "scada tag name/rmm plugin name@sensor name",
                      "type": "Float",
                      "size": "4",
                      "readWrite": "R",
                      "precision": "3.2",
                      "defaultValue": "0.00",
                      "minimum": "-99.99",
                      "maximum": "199.99"
                    }
                  ]
                }
              ]
            },
            {
              "gatewayId": "xxx",
              "gatewayName": "xxx",
              "iotSense": {
                "type": "EdgeX",
                "groupId": "APMId",  // EdgeX填写APM ID
                "groupName": "groupName"
              },
              "devices": [
                {
                  "deviceId": "Scada/RMM deviceId",
                  "deviceName": "exampleDeviceName(RMM: AgentName/Scada: deviceName)",
                  "deviceProfileName": "xx",
                  "tags": [
                    {
                      "name": "temp",
                      "tag": "scada tag name/rmm plugin name@sensor name",
                      "type": "Float",
                      "size": "4",
                      "readWrite": "R",
                      "precision": "3.2",
                      "defaultValue": "0.00",
                      "minimum": "-99.99",
                      "maximum": "199.99"
                    }
                  ]
                }
              ]
            }
          ]
        }
      }
      ```

    * 產生SCADA config部分
      * 先不修改

* DataAgent
  * 一個EdgeX改成一個manager減少iothub的connection數
* mongodb schema - wisepaasSetting

```
{
  "_id": "5ca1a94e6a34081a3ba956cc",
  "enabled": false,
  "publishInterval": 10,
  "srpType": "scada",
  "srpId": "73b668ec-7966-4154-87cd-4ae82c9b9883",
  "iotkey": "aa2bda0246fef2fbe6e361b5a8c4bdv0",
  "credentialUrl": "https://api-dccs.wise-paas.com/",
  "gateways": [
    {
      "gatewayId": "5ca1a9186a34081a3ba95550",
      "gatewayName": "SCADA_TEST",
      "devices": [
        {
          "deviceId": "5bd91cdc9f8fc2000160b0d2",
          "deviceName": "JC.RR5.NAE9.ConfRoom.Padre.Island01",
          "deviceProfileName": "JC.RR5.NAE9.ConfRoom.Padre.Island",
          "tags": [
            {
              "name": "AnalogInput_3000290",
              "deadband": 0,
              "tag": "AnalogInput_3000290",
              "type": "Float",
              "size": "5",
              "readWrite": "R",
              "precision": "3.2",
              "defaultValue": "0.00",
              "minimum": "-99.99",
              "maximum": "199.99"
            },
            {
              "name": "AnalogOutput_3000289",
              "deadband": 0,
              "tag": "AnalogOutput_3000289",
              "type": "Float",
              "size": "5",
              "readWrite": "R",
              "precision": "3.2",
              "defaultValue": "0.00",
              "minimum": "-99.99",
              "maximum": "199.99"
            },
            {
              "name": "enableRandomization",
              "deadband": 0,
              "tag": "enableRandomization",
              "type": "Boolean",
              "size": "1",
              "readWrite": "W",
              "precision": "",
              "defaultValue": "true",
              "minimum": "",
              "maximum": ""
            },
            {
              "name": "collectionFrequency",
              "deadband": 0,
              "tag": "collectionFrequency",
              "type": "Integer",
              "size": "4",
              "readWrite": "W",
              "precision": "3",
              "defaultValue": "15",
              "minimum": "0",
              "maximum": "600"
            }
          ]
        }
      ]
    }
  ]
}
```

### 沿伸議題



