# API Key

---

**API 金鑰\(API Key\)**，

是一種讓客戶端在發送請求時，讓客戶端依據其認證資訊計算簽章，

再將簽章及認證資訊連同請求一併送出，而服務端接收請求後，會對簽章及認證資訊進行驗證的認證方式。

## 運作方式

### 客戶端流程：

1. 客戶端向服務端完成註冊後，會從服務端取得 api\_key 及 security\_key 。
2. 客戶端請求存取資源時，根據 api\_key、security\_key、timestrap、URI，採用 HMAC-SHA256，計算出雜湊值 sign，並將此雜湊值作為簽章 。
3. 將 api\_key、timestrap、sign 連同請求參數發送給服務端。

### 服務端流程：

1. 服務端接收請求後，首先驗證 api\_key 是否存在，若存在則獲取該 api\_key 的 security\_key。
2. 接著驗證 timestrap 是否超過時間限制。
3. 依據接收到的 api\_key、security\_key、timestrap，加上客戶請求的 URI，採用與客戶端計算簽章相同的計算方式計算出簽章值
4. 最後，將計算出的簽章值與客戶端發送的簽章值進行校驗。

## 範例

### 客戶端流程：

![](http://fanli7.net/uploads/allimg/2016-05-16/2015101611045213385client.png)

### 服務端流程：

![](http://fanli7.net/uploads/allimg/2016-05-16/2015101611045762856server.png)

