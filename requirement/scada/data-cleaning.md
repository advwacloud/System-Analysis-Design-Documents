# Data Cleaning

---

### 目標

* 為了避免資料量一直無限制的增加, 所以新增可設定的Data Cleaning Interval. 定時清理歷史資料

### 修改幅度

* Portal
  * System Setting 加入參數 DATA\_CLEANING\_INTERVAL
  * System/params API
  * 修改完通知dataworker
* Postgresql
  * sys\_paramters
    * DATA\_CLEANING\_INTERVAL
      * 單位:天, 預設值30



