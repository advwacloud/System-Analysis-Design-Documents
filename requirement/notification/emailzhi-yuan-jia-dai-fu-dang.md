# Email支援夾帶附檔

---

### 目標

* 讓使用者呼叫send/directsend API時可以夾帶多個檔案\(最大限制5個, 總共限制10MB\)

### 修改幅度

* API

  * 參數 attachments \(object array\)

    * name: 檔案名稱
    * content: 呼叫者將內容轉成binary後用Base64轉碼, api解碼後發送

    ```
    attachments: [{
      "filename": "file1.png",
      "content":"xxxxxxxx"
    }, {
      "filename": "file2.pdf",
      "content":"yyyyyy"
    }]
    ```

### 沿伸議題



