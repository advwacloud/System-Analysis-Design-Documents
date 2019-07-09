# 整合WhatsApp

---

### 目標

* 讓使用者可以透過WhatsApp發送通知

### 修改幅度

* 參考 Sammi的Survey文件 
  * [https://advwacloud.quip.com/slKvAlDeNLsz](https://advwacloud.quip.com/x12cA3Nicqvf/WhatsApp-Cloud-API-Wassenger)

### 沿伸議題

* WhatsApp官方目前無開放API, 所以採用第三方Wassenger服務來達成目的

* Wassenger訊息發送是先將訊息送進到Queue中依序執行, 但是若連續訊息中某個訊息發送失敗, 就可能造成訊息內容錯亂不連續



