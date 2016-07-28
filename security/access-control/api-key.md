## API Key

---

**API 金鑰\(API Key\)**，

是一種讓客戶端在發送請求時，將認證資訊以參數形式附加在 URI 之後，再由服務端接收請求，並對認證資訊進行驗證的認證方式。

## 運作方式

### 客戶端流程：

1. 客戶端向服務端完成註冊後，會從服務端取得 api\_key 及 security\_key。
2. 客戶端請求存取資源時，根據 api\_key、security\_key、timestrap、rest\_uri，採用安全雜湊演算法\(SHA256\)，計算出雜湊架構訊息驗證碼\(Hash-based Message Authentication Code，簡稱 HMAC\) ，將此雜湊值作為簽章 sign 。
3. 將 api\_key、timestrap、sign 附加在 URI 之後，發送給服務端。

### 服務端流程：

1. 服務端接收請求後，首先驗證 api\_key 是否存在，若存在則獲取該 api\_key 的 security\_key。
2. 接著驗證 timestrap 是否超過時間限制。
3. 依據接收到的 api\_key、security\_key、timestrap，加上客戶請求的 URI，採用與客戶端計算簽章相同的計算方式計算出簽章值
4. 最後，將計算出的簽章值與客戶端發送的簽章值進行校驗。

## 範例：

### 客戶端

![](http://fanli7.net/uploads/allimg/2016-05-16/2015101611045213385client.png)

### 服務端

![](http://fanli7.net/uploads/allimg/2016-05-16/2015101611045762856server.png)

