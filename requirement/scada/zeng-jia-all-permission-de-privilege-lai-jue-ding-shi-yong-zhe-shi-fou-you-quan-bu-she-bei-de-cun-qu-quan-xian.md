# 增加 all\_permission 的 Privilege 來決定使用者是否有全部設備的存取權限

---

### 目標

* 與SSO role脫離, 讓使用者自主彈性分配權限

### 修改幅度

* Portal前端

  * 若user有all\_permission, 則permission無法修改

* API

  * 改為根據all\_permission來決定是否要檢查DeviceRight

* DB

  * retention\_policy\_list
    * name: varchar \(32\)
    * description: varchar \(256\)
    * duration: int, default: 90
  * device\_list.retention\_policy
    * varchar\(32\), deafult: ""

### 沿伸議題

* 


