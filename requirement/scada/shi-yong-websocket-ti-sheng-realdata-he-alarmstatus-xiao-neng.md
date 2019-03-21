# 使用WebSocket提升RealData和AlarmStatus效能

---

### 目標

* 為了避免Portal一直long pulling API造成系統負擔

### 修改幅度

* RealData
  * 前端
    * 使用者進入到Tag List頁面, 則開始與後端建立Socket連線, 連線成功時發送要訂閱的tag list
    * 使用者離開Tag List頁面, 則與後端Socket連線断開
  * 後端
    * 收到新的cilent訂閱時, 把訂閱的client和tag list加入管理, 並與原本要查詢的total tag list聯集, 當發現值有改變, 則主動發送給對應的client
    * 發現client離開時, 把該client訂閱的tag list從total tag list移除
      * 可以考慮用lodash把client清單中的各個tag list重新聯集一次產生新的total tag list

### 沿伸議題

* Dataworker目前在記憶體有保存last value, 所以Web Socket做在Dataworker會不會更好?
  * Multi-instance下記憶體的last value不會一致, 怎麼處理?



