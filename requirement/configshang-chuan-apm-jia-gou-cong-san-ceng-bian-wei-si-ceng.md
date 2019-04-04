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
    * APM
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
    * SCADA
      * 先不修改
* DataAgent
  * 一個gateway一個manager的架構不用修改, 但每個manager都是使用同一組DCCS來連線

### 沿伸議題



