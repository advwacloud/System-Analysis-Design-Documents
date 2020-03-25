# 增加 all\_permission 的 Privilege 來決定使用者是否有全部設備的存取權限

---

### 目標

* 與SSO role脫離, 讓使用者自主彈性分配權限

### 修改幅度

* Portal前端

  * 若user有all\_permission, 則permission無法修改

* API

  * 改為根據all\_permission來決定是否要檢查DeviceRight
  * 將user scope加入到user token cahe來減少DB查詢, 但是如果user scope被調整必須將user token cache整個清除

* DB

  * scope table增加 all\_permission

### 沿伸議題

* 


