# Json Web Token

---

**Json Web 權杖 \(Json Web Token , 簡稱 JWT \)**， 是 JSON 型安全性權杖加密，

能夠使身分和安全性資訊在安全性網域之間共用。

可以被用來在身份提供者和服務提供者間傳遞被認證的用戶身份訊息，以便於從資源服務器獲取資源。

## 權**杖結構**

JWT 共分為三個部分，頭部\(Header\)、載荷\(Payload，也可稱為 Claim set\)、簽證\(Signature\)，
三個部分之間以句號 . 串接後，即組成完整的 JWT。

![](http://blog.nsfocus.net/wp-content/uploads/2015/10/jwt.png)

### 頭部**\(Header\)**

用來描述 **JWT** 的基本訊息，例如其類型或簽名所用的演算法。

包括兩個訊息欄位：typ 指明 Token 的類型，alg 則說明簽名所用的演算法。

先定義頭部的 JSON 結構

```
 header = {
     "typ": "JWT",        # 聲明類型是 JWT
     "alg": "HS256"       # 聲明簽名所用的加密演算法是 HS256
 }
```

接著以 Base64 的方式編碼

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9
```

### **載荷\(Payload**，也可稱為** Claim set\)**

載荷就是存放有效訊息的地方。就像是飛機上承載的貨品，這些有效訊息包含三個部分

* 標準中註冊的聲明，包含以下訊息欄位：

  * iss：JWT 的簽發者
  * sub：JWT 所面向的用戶
  * aud：JWT 的接收方
  * iat：JWT 的簽發時間
  * exp：JWT 的過期時間，這個過期時間必須要大於簽發時間
  * nbf：定義在什麼時間之前，該 JWT 都是不可用的.
  * jti：JWT 的唯一身份標識，主要用來作為一次性的權杖，從而迴避[重放攻擊](https://zh.wikipedia.org/wiki/%E9%87%8D%E6%94%BE%E6%94%BB%E5%87%BB)。

* 公共的聲明，可以添加任何的訊息，一般添加用戶的相關信息或其他業務功能需要的必要信息，不建議添加敏感信息，因為該部分在客戶端可解密.

* 私有的聲明，是服務端和客戶端所共同定義的聲明，一般不建議存放敏感信息，因為 base64 是對稱解密的，意味著該部分信息可以歸類為明文信息。


先定義載荷的 JSON 結構

```
payload = {
    "iss": "http://example.org",
    "aud": "http://example.com",
    "iat": 1356999524,
    "exp": 1357000000
}
```

接著以 Base64 的方式編碼

```
eyJpc3MiOiJodHRwOi8vZXhhbXBsZS5vcmciLCJhdWQiOiJodHRwOi8vZXhhbXBsZS5jb20iLCJpYXQiOjEzNTY5OTk1MjQsImV4cCI6MTM1NzAwMDAwMH0
```

### 簽證**\(Signature\)**

會先將標頭和載荷的原始內容分別以 **Base64** 的方式編碼，以 **句號 .  **串接後，再以標頭指定的演算法搭配金鑰進行加密，

而得到簽名內容：

```
Signature = HMACSHA256(
    base64UrlEncode(header) + “." + base64UrlEncode(payload),
    secret
)
```

### 運作方式

### 客戶端流程：

1. 客戶端先向服務端註冊，並取得 JWT 。

  ```
  token = encodeBase64(header) + '.' + encodeBase64(payload) + '.' + Signature
  # token is:
  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vZXhhbXBsZS5vcmciLCJhdWQiOiJodHRwOi8vZXhhbXBsZS5jb20iLCJpYXQiOjEzNTY5OTk1MjQsImV4cCI6MTM1NzAwMDAwMH0.YgUDoK-kIzdrSa0pph5rkW1wsv0FaOX6fXvl-5chpOc
  ```

2. 客戶端發送請求時，在標頭欄位設定認證資訊：

  ```
  Authorization: Bearer <token>
  ```


### 服務端流程

1. 根據 JWT 的簽名部分，驗證頭部及載荷的內容。
2. 從頭部及載荷取得用戶資訊，依據用戶資訊進行認證。 



### 流程圖

![](https://i2.read01.com/image.php?url=0D5sm801)

