# 歷史資料預處理

---

### 目標

* 將RawData聚合成分, 時, 日資料另外儲存在其它collection, 避免每次查詢都是從RawData重新計算, 耗費大量的mongodb效能.

### 修改幅度

* ETL
  * 分資料排程
    * 每一個整分執行, 將前一分的歷史資料分別計算LAST, AVG, MAX, MIN後, 另存於scada\_HistMinData
  * 時資料排程
    * 每一個整時執行, 將前一小時的歷史資料分別計算LAST, AVG, MAX, MIN後, 另存於scada\_HistHourData
  * 日資料排程
    * 每一個整日執行, 將前一日的歷史資料分別計算LAST, AVG, MAX, MIN後, 另存於scada\_HistDayData
  * 先不考慮前一日以前的資料處理, 避免處理過於耗時
* Utility

  * 根據intervalType決定去哪個collection撈取資料
  * mongodb schema \(分時日的都相同\)

    ```
    let histMinDataSchema = new Schema({
      _id: {
        type: Schema.Types.ObjectId
      },
      s: String,
      t: String,
      sum: Object,
      count: Object,
      avg: Object,
      max: Object,
      min: Object,
      last: Object,
      ts: {
        type: Date,
        default: Date.now
      }
    }, { collection: 'scada_HistMinData', versionKey: false });

    histMinDataSchema.index({ _id: 1 }, { unique: true });

    mongoose.model('HistMinData', histMinDataSchema);
    ```

### 沿伸議題

* 使用者可能沒辦法看很即時的資料, 若是看日資料可能會只能看到前一日以前的資料 \(因為當日還未計算\).



