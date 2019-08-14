# 訊息重送功能

---

### 目標

* 目前訊息失敗後, 並無重送功能, 容易因為可能偶爾網路不穩定導致訊息就永遠通知不到對方

### 修改幅度

* send/directsend API發送失敗後, 將message寫入到mongodb, 並記錄重送次數
* 每隔一段時間\(1 min\), pigeon-breeder會掃描一次mongodb是否有待重送的message, 若有, 則重新發送
  * 重送成功: 將status改為sucess, expire time設為0, 讓mongodb自動清除

  * 重送失敗: retryCount + 1, 重試三次後停止重送, 將status改為failed, expire time設為0, 讓mongodb自動清除

### 沿伸議題

* 每次重送過程都需要被記錄下來 \(下一個功能\)





