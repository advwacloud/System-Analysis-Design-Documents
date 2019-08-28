# 支援SMS簡訊通知

---

### 目標

* 整合clickatell服務, 讓使用者可以發送SMS簡訊通知

### 修改幅度

* clickatell的API主要有分成兩種類型, HTTP和REST, 但設定SMS integration時只能擇一, 要試看看是否兩種同時都能用,  若可以, 程式邏輯使用REST

* 參考

  * [https://www.clickatell.com/](https://www.clickatell.com/)
  * [https://advwacloud.quip.com/plZJAMQ1LmLZ/SMS-Clickatell](https://advwacloud.quip.com/plZJAMQ1LmLZ/SMS-Clickatell)

  * [https://archive.clickatell.com/developers/api-docs/?\_ga=2.21387835.1898727926.1566956402-1464451373.1562651596](https://archive.clickatell.com/developers/api-docs/?_ga=2.21387835.1898727926.1566956402-1464451373.1562651596)

### 沿伸議題

* 是否會需要整合其它SMS provider, 例如: 不同地區有不同的Provider, 系統該如何處理?
  * SMS UI增加Provider選項, 根據選項改變UI配置!? 



