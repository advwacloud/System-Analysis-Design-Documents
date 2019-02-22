# 自訂訊息範本

---

### 目標

* 讓開發者可以預先設定好訊息範本, 好處是串接的應用程式不需要額外開介面定義訊息格式
* 範本編輯介面
  * Email: 一般文字編輯器和HTML編輯器兩種
    * HTML編輯器: [https://surmon-china.github.io/vue-quill-editor/](https://surmon-china.github.io/vue-quill-editor/)
  * LINE: 一般文字編輯器
  * WeChat: 一般文字編輯器
  * Webhook: 一般文字編輯器 \(已完成\)

### 修改幅度

* Portal
  * 頁面 UI: [https://balsamiq.cloud/sxls649/plenlvu](https://balsamiq.cloud/sxls649/plenlvu)
* API & Postgresql
  * template欄位
* Utility
  * 根據send傳入的變數從template找出對應的將其取代
    * template: &lt;b&gt;Hello {name} !&lt;/b&gt;
    * send: {name: 'Steven'}
    * replaced result: &lt;b&gt;Hello Steven !&lt;/b&gt;

### 沿伸議題



