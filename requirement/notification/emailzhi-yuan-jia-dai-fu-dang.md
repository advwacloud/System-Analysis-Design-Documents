# Email支援夾帶附檔

---

### 目標

* 讓使用者呼叫send/directsend API時可以夾帶多個檔案\(最大限制5個, 總共限制10MB\)

### 修改幅度

* API

  * 參數 files \(object array\)

    * name: 檔案名稱
    * content: 呼叫者將內容轉成binary後用Base64轉碼

    ```
    files: [{
      "name": "file1",
      "content":"xxxxxxxx"
    }, {
      "name": "file2",
      "content":"yyyyyy"
    }]
    ```

### 沿伸議題



