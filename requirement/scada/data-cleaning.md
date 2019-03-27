# Data Cleaning

---

### 目標

* 為了避免資料量一直無限制的增加, 所以新增可設定的Data Cleaning Interval. 定時清理歷史資料

### 修改幅度

* Portal
  * System Setting 加入參數
    * DATA\_RETENTION\_DAYS

    * DATA\_CLEANING\_ENABLED

    * DATA\_CLEANING\_TIME
  * System/params API
  * 修改完通知dataworker
* Postgresql
  * sys\_paramters
    * DATA\_RETENTION\_DAYS

      * 單位:天, 預設值90

    * DATA\_CLEANING\_ENABLED
      * 預設值true
    * DATA\_CLEANING\_TIME
      * 預設值01:05 \(24小時制\)



