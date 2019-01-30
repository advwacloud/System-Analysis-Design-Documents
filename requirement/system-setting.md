# System Setting \(for WISE-PaaS SCADA\)

---

### 目標

* 因為有些功能需要呼叫到WISE-PaaS的服務\(Notification\), 但必須有SSO帳號權限

  * 讓使用者設定一組對外呼叫API所使用的SSO帳號

* 增加Dashboard和Notification URL設定

  * 沒有設定或設定為空則預設使用同space下的Dashboard和Notification URL

* 增加System Setting頁面, 有system\_setting權限的人才看的到

### 

### 修改幅度

* Portal
  * System Setting 頁面 UI: [https://balsamiq.cloud/sxls649/plenlvu](https://balsamiq.cloud/sxls649/plenlvu)
  * System/params API
  * 修改完通知dataworker
* Postgresql
  * sys\_paramters
    * SSO\_USERNAME
    * SSO\_PASSWORD
    * DASHBOARD\_GRAFANA\_URL
    * NOTIFICATION\_SERVICE\_URL
    * MESSAGE\_RULE\_MONGODB\_SETTING \(for 客製化mongodb schema\)
* 增加system\_setting permission

### 

### 沿伸議題

* Apps間溝通機制如何實作成標準介面?

* 通知方式用MQTT是否合適?

  * MQTT: multi-instance subscribe後都可以同時收到

  * API:沒有broker轉發, multi-instance下需要API gateway



