# 資料重覆性檢查機制

---

### 目標

* 為了避免地面端重覆拋送同樣的資料塞滿MongoDB

### 修改幅度

* Dataworker
  * 記錄每個tag的last value, 下次值收到值後比對是否相同

### 沿伸議題

* Multi-instance情境下
  * 不可能每個instance都去保存同樣的tag last value, 最終會塞爆每個instance記憶體
    * Redis cache



