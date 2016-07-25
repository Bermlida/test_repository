# Access Control

---

訪問控制REST API需要清晰定義哪些操作能夠公開訪問，哪些操作需要授權訪問。一般而言，如果對REST API的安全性要求比較高，那麼，所有的API的所有操作均需得到授權。在HTTP協議之上處理授權有很多方法，如HTTP BASIC Auth，OAuth，HMAC Auth等，其核心思想都是驗證某個請求是由一個合法的請求者發起。 Basic Auth會把用戶的密碼暴露在網絡之中，並非最安全的解決方案，OAuth的核心部分與HMAC Auth差不多，只不過多了很多與token分發相關的內容。這裡我們主要講講HMAC Auth的思想。回到Security的三個屬性：一致性，機密性，和可用性。 HMAC Auth保證一致性：請求的數據在傳輸過程中未被修改，因此可以安全地用於驗證請求的合法性。HMAC主要在請求頭中使用兩個字段：Authorization和Date（或X-Auth-Timestamp）。 Authorization字段的內容由":"分隔成兩部分，":"前是access-key，":"後是HTTP請求的HMAC值。在API授權的時候一般會為調用者生成access-key和access-secret，前者可以暴露在網絡中，後者必須安全保存。當客戶端調用API時，用自己的access-secret按照要求對request的headers\/body計算HMAC，然後把自己的access-key和HMAC填入Authorization頭中。服務器拿到這個頭，從數據庫（或者緩存）中取出access-key對應的secret，按照相同的方式計算HMAC，如果其與Authorization header中的一致，則請求是合法的，且未被修改過的；否則不合法。

