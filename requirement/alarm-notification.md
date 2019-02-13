# Alarm Notification \(for WISE-PaaS SCADA\)

---

### 目標

* Dataworker偵測tag value超過警報範圍, 則標記為報警, 之後觸發設定的Notification

* Portal可供使用者設定要發送的Notification Group \(總共最多3組\), 支援以下event \(不允許相同Event下有相同Group的設定\)

  * Happened

  * Acked

  * Cleared

### 修改幅度

* Dataworker若觸發alarm, 呼叫send API \(需要先實作SSO帳號設定\)
* Portal
  * UI: [https://balsamiq.cloud/sxls649/plenlvu](https://balsamiq.cloud/sxls649/plenlvu)

### 

### 沿伸議題



