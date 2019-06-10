# Data Archive

---

### 目標

* 讓使用者選擇想要備份的篩選條件, 並詢問是否要刪除原本的資料, 系統進行歷史資料備份到blob
  * 篩選條件
    * 時間區間 \(必選\)
    * SCADA

### 修改幅度

* UI
  * System Setting增加Data Archive子功能
* API
  * 增加archive POST API
* Utility

  * Publish message到AMQP queue, 讓dataworker處理

### 沿伸議題

* 將Dataworker資料處理功能都搬移到ETL以符合微服務概念
  * 增加memory使用量, 是否可以被接受?



