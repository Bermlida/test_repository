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
   "label": "Food",
   "items_url": "/api/items?category=1",
   "brands" : [
         {
            "label" : "友臣",
            "brand_key" : "32073",
            "url" : "/api/brands/32073"
         }, {
            "label" : "乐事",
            "brand_key" : "56632",
            "url" : "/api/brands/56632"
         }
         ...
   ],
   "hot_searches" : …
}
```

