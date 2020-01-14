# DeviceId自動生成

---

### 目標

* 減少階層, 可以減少資料儲存量和API傳輸量, 加速資料庫寫入/查詢效能

### 修改幅度

### 沿伸議題

* DeviceId在multi-worker時如何自動產生? 可能每個instance同時都有在處理相同config封包

  * 使用ScadaId和地端上傳的DeviceName hash成唯一的DeviceId

* 副作用

  * Dashboard/Composer所儲存的deviceId必須轉換

  * EnSaaS 3.0的mongodb和influxdb需要mirgation

  * 直接存取DB的SRP需要修改邏輯



