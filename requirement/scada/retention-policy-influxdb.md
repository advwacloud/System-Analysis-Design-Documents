# Retention Policy \(Influxdb\)

---

### 目標

* 讓使用者建立InfluxDB的retention policy, 並綁定device, 讓InfluxDB對資料做循環刪除, 避免資料塞爆DB

### 修改幅度

* Portal
  * 增加顯示RP list, 時間不夠的話先不做綁定設備功能

* Utility

  * getRetentionPolicies 取得influxdb所有rp list
  * datastore init 啟動時, 若是用influxdb就先去建立"90days" RP
  * scada/device status 固定用"90days" RP去寫入和查詢

* Edge SDK
  * device config增加RetentionPolicy欄位\(填RP name\), 預設為空
* DB
  * device\_list.retention\_policy
    * string, deafult: ""
* Worker
  * 接收到config, 

### 沿伸議題

* 


