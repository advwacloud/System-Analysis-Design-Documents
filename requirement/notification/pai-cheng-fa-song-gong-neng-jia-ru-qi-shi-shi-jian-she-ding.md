# 排程發送功能加入起始時間設定

---

### 目標

* 讓使用者可以設定排程起始時間\(日期,時,分\)

### 修改幅度

* DB & API
  * level\_list 多一個欄位: start\_time \(DateTime\)
* Utility
  * 若group被設定intveral &gt; 0, 則把timer啟動時間改為設定的起始時間
* UI
  * 預設是Now

![](/assets/level.png)

![](/assets/comDateTime.png)

* ### 沿伸議題
* 


