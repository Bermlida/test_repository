# **HATEOAS**

---

**使用超媒體作為應用狀態的引擎 \( Hypermedia as the engine of application state** ，簡稱 **HATEOAS \)**，

是 REST 所提及的約束「一致性的操作界面」中所包括的子項目之一，

服務端所傳遞給客戶端的回應訊息需要提供足夠用於操作該資源的訊息，具體而言包括以下幾個方面：

* 如何對該資源進行新增，修改以及刪除等操作行為。

* 如何透過該資源去存取、操作其他相關的各項資源。


## 範例

假設客戶端打算獲取一項產品編號為 20 的產品資料，並已透過服務端取得了回應結果，

而回應結果如下：

```
{
   "uri": "/products/20",
   "category": "Mobile",
   "brand": {
      "uri": "/brands/256",
      "name": "InFocus",
      "description": "An US electronics company."
   },
   "accessories_url": "/products/20/accessories",
   "actions": ["GET", "PUT"]
}
```

上述 JSON 結構，欄位定義如下：

* uri
  該資源所對應之資源標識符，可以搭配 actions 欄位協助客戶端進一步操作該資源。
* category
  產品分類，是該資源自身的資料欄位。
* brand
  產品品牌，品牌是與產品相關的其他資源，因此提供該資源的 URI 協助客戶端進一步操作；name 與 description 則是該資源的相關訊息。
* accessories\_url
  產品配件，配件是與產品相關的其他資源，也是產品包含的其他資源，提供該產品包含的配件列表的 uri，協助客戶端存取該產品的相關配件
* actions
  可以用於該資源的一系列操作行為，除了這些行為外，其他的操作行為均不可用於該資源。

