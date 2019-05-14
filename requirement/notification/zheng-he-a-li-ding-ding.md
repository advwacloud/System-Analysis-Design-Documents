# 整合阿里釘釘

---

### 目標

* 讓使用者可以透過阿里釘釘發送通知

### 修改幅度

* 參考 Eryn的Survey文件 
  * [https://advwacloud.quip.com/slKvAlDeNLsz](https://advwacloud.quip.com/slKvAlDeNLsz)
* Portal \(介面與WeChat類似\)

  * DingTalk Service Setting

    * AgentId, AppKey, AppSecret

  * Member List

    * First Name, Last Name, ID, Type \(下拉式選單: user/department, 預設user\)

### 沿伸議題

* accessToken有過期時間\(7200秒\), 必須自己實作refresh token機制

* 群發送需要的chatId必須要使用者用釘釘的開發工具, 而且必須是建立群的人才能取得 \(暫不實作\)

  * [https://bbs.aliyun.com/read/281925.html?spm=a2c4e.11155515.0.0.679253467j7QyQ](https://bbs.aliyun.com/read/281925.html?spm=a2c4e.11155515.0.0.679253467j7QyQ)



