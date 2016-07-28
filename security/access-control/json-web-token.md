# Json Web Token

---

**Json Web 權杖 \(Json Web Token , 簡稱 JWT \)**， 是 JSON 型安全性權杖加密，

能夠使身分和安全性資訊在安全性網域之間共用。

可以被用來在身份提供者和服務提供者間傳遞被認證的用戶身份訊息，以便於從資源服務器獲取資源。

## 權**杖結構**

![](http://blog.nsfocus.net/wp-content/uploads/2015/10/jwt.png)

### 頭部**\(Header\)**

用來描述 **JWT** 的基本訊息，例如其類型或簽名所用的演算法。

在範例中，typ 指明 Token 的類型是 JWT，alg 則說明簽名所用的演算法是 HS256：

```
 {
     "typ": "JWT",        # 聲明類型
     "alg": "HS256"       # 聲明簽名所用的加密演算法 
 } 
```

### **載荷\(Payload**，也可稱為** Claim set\)**

此部份是 **JWT** 的主要資料部分\(本文\)，

可依實際需要增減欄位內容，可用的欄位定義在[規範文件](https://tools.ietf.org/html/rfc7519)都找得到。

範例欄位定義如下：

* iss：JWT 的簽發者
* aud：JWT 的接收方
* iat：簽發 JWT 時的時間戳記
* exp：JWT 什麼時候過期

```
{
    "iss": "http://example.org",
    "aud": "http://example.com",
    "iat": 1356999524,
    "exp": 1357000000
}
```

### 簽證**\(Signature\)**

會先將標頭和載荷的內容分別以 **Base64** 的方式編碼，以 **句號 .  **串接後，

再以標頭指定的演算法搭配金鑰進行加密，而得到簽名內容：

```
HMACSHA256(
    base64UrlEncode(header) + “." + base64UrlEncode(payload),
    secret
)
```

最後，再將標頭、載荷、簽名三個部分各別以 **Base64** 的方式編碼 ，之間以 **句號 .  **串接後，即獲得 **JWT** 的完整內容：

```
token = encodeBase64(header) + '.' + encodeBase64(payload) + '.' + encodeBase64(signature)
# token is:
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vZXhhbXBsZS5vcmciLCJhdWQiOiJodHRwOi8vZXhhbXBsZS5jb20iLCJpYXQiOjEzNTY5OTk1MjQsImV4cCI6MTM1NzAwMDAwMH0.YgUDoK-kIzdrSa0pph5rkW1wsv0FaOX6fXvl-5chpOc
```

發送請求時，在標頭欄位設定認證資訊：

```
Authorization: Bearer <token>
```

