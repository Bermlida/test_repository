# Access Control

---

**Access Control **指的是訪問控制，

客戶端\(Client\)使用**統一資源標識符\(URI\)**訪問想要存取的資源\(Resource\)，

透過指定請求方法\(Request methods\)對資源進行特定的操作行為。

然而，有些資源是受保護的，必須經過授權才能訪問從而進行操作，有些資源則是公開的，能夠公開訪問，

也因此，RESTful API 需要清晰定義哪些資源能夠公開訪問，哪些資源需要授權訪問才能訪問。

針對那些受保護的資源，客戶端\(Client\)必須得到授權才能進一步針對該資源進行操作，

針對RESTful API ，處理授權有很多方法，如HTTP BASIC Auth，OAuth，HMAC Auth等，其核心思想都是驗證某個請求是由一個合法的請求者發起。 

Basic Auth會把用戶的密碼暴露在網絡之中，並非最安全的解決方案，

OAuth的核心部分與HMAC Auth差不多，只不過多了很多與token分發相關的內容。

這裡我們主要講講HMAC Auth的思想。回到Security的三個屬性：一致性，機密性，和可用性。 HMAC Auth保證一致性：請求的數據在傳輸過程中未被修改，因此可以安全地用於驗證請求的合法性。HMAC主要在請求頭中使用兩個字段：Authorization和Date（或X-Auth-Timestamp）。 Authorization字段的內容由":"分隔成兩部分，":"前是access-key，":"後是HTTP請求的HMAC值。在API授權的時候一般會為調用者生成access-key和access-secret，前者可以暴露在網絡中，後者必須安全保存。當客戶端調用API時，用自己的access-secret按照要求對request的headers\/body計算HMAC，然後把自己的access-key和HMAC填入Authorization頭中。服務器拿到這個頭，從數據庫（或者緩存）中取出access-key對應的secret，按照相同的方式計算HMAC，如果其與Authorization header中的一致，則請求是合法的，且未被修改過的；否則不合法。

