# Json Web Token

---

Json Web Token, 簡稱 JWT

是為了在網路應用環境間傳遞聲明而執行的，一種基於 JSON 的開放標準。

一般被用來在身份提供者和服務提供者間傳遞被認證的用戶身份訊息，以便於從資源服務器獲取資源，

也可以增加一些額外的其它業務邏輯所必須的聲明訊息，可以直接被用於認證，也可被加密。

### 範例

第一部分是 標頭\(Header\)，用來描述 JWT 的基本訊息，例如其類型或簽名所用的演算法

在範例中，typ 指明 Token 的類型是 JWT，alg 則說明簽名所用的演算法是 HS256

```
 {
     "typ": "JWT",
     "alg": "HS256"
 } 
```

第二部分是 載荷\(Payload，也可稱為 Claim set\) ，

此部份是 JWT 的主要資料部分，

可依實際需要增減欄位內容，可用的欄位定義在[規範文件](https://tools.ietf.org/html/rfc7519)都找得到

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

第三部分是 簽名\(Signature\)，

會先將標頭和載荷的內容分別以 Base64 的方式編碼，以句號 . 串接後，

再以標頭指定的演算法搭配金鑰進行加密，而得到簽名內容

```
HMACSHA256(
    base64UrlEncode(header) + “." + base64UrlEncode(payload),
    secret
)
```

最後，再將標頭、載荷、簽名三個部分各別以 Base64 的方式編碼 ，之間以句號 . 串接後，即獲得 JWT 的完整內容

```
token = encodeBase64(header) + '.' + encodeBase64(payload) + '.' + encodeBase64(signature)
# token is:
:
```





