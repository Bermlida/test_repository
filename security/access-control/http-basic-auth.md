# HTTP Basic Authentication

---

**HTTP基本認證\(HTTP Basic Authentication\)**，

是一種用來允許 Web 瀏覽器或其他客戶端程序在請求時提供包含用戶名和密碼的身份憑證進行登錄驗證的方式。

會在用戶名的後方加上 **冒號\(colon\) :** ，然後串接上密碼，再將得出的結果字串以 **Base64** 的方式編碼，最終將其發送出去。

接收者解碼後會得到一個由冒號分隔的用戶名和密碼的字串。

### 範例

假設，**客戶端\(Client\) **提供的用戶名稱是 client，密碼是 secret，則拼接後的結果如下：

`client:secret`

接著，再將字串用Base64編碼，得到字串如下：

`Y2xpZW50OnNlY3JldA==`

然後發送請求，在標頭欄位設定認證資訊：

`Authorization: Basic Y2xpZW50OnNlY3JldA==`

於是，**服務端\(Server\)** 接收請求後，依據標頭設定的認證資訊進行解碼再驗證，即完成認證工作。

