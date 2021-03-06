# Retention Policy \(Influxdb\)

---

### 目標

* 讓使用者建立InfluxDB的retention policy, 並綁定device, 讓InfluxDB對資料做循環刪除, 避免資料塞爆DB

### 修改幅度

* Portal前端

  * 增加顯示RP list \(類似scada list 表格即可\), 並可以綁定設備

* API

  * GET /RetentionPolicy
  * GET /RetentionPolicy/{name}
  * POST /RetentionPolicy
    * { name: "180days", description: "180 days",  duration: 180, devices: \[{ scadaId: "", deviceId: "" }\] }
    * description和devices非必填
  * PUT /RetentionPolicy/{name}
    * { description: "180 days", duration: 180, devices: \[{ scadaId: "", deviceId: "" }\] }
    * 名字只能新增不能修改
  * DELETE /RetentionPolicy/{name}
  * 必須記錄每個device的RP name在memory, 呼叫utility查詢需要帶入

* Utility

  * datastore init 啟動時, 若是用influxdb就先去建立"90days" RP
  * scada/device status 固定用"90days" RP去寫入和查詢 \(不受data cleaning影響\)
  * dataHelper都根據DATA\_CLEANING\_ENABLED決定是否要用外部傳入的rp name

* Edge SDK

  * device config增加RetentionPolicy欄位\(填RP name\), 預設為空

* DB

  * retention\_policy\_list
    * name: varchar \(32\)
    * description: varchar \(256\)
    * duration: int, default: 90
  * device\_list.retention\_policy
    * varchar\(32\), deafult: ""

* Worker

  * 接收到config, 寫入rp name到db
  * 必須記錄每個device的RP name在memory, 呼叫utility 寫入時需要帶入

### 沿伸議題

* 


