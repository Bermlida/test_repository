## Resource Identification

---

Web服務\(Web service\)** **是一種 **服務導向架構\(Service-oriented architecture\)**，而服務導向架構指的是將應用程式功能作為服務發送給最終用戶或者其他服務；相較現行的Web服務而言，RESTful API 實現了 REST 設計風格，改以 **資源導向架構\(Resource-oriented architecture\) **來設計 API 。

也因此，在Web服務中提供的各式介面，這些介面常常表達了某個動作，例如將商品放入購物車、送出訂單等之類的。這一系列動作組合在一起就可以組成完成目標所需要執行的業務邏輯。在需要調用這些介面的時候，客戶端需要向這些介面所在的 URL 發送一個請求，從而驅使服務執行該動作。

而在 RESTful API 中，所提供的各個介面則是一系列不同的資源，而業務邏輯需要通過對資源的操作行為來完成。換言之，RESTful API 將不再以執行了什麼動作為中心，而是以資源為中心，對資源的操作行為例如新增，查詢，修改，刪除，以及對符合特定條件的資源進行的列表操作則與其分離。

## 範例

假設現在要針對產品編號為 20 的產品資料，進行查詢、修改、刪除：

在Web服務中往往會是這樣的：

```
/getProducts/20       # 查詢
/updateProducts/20    # 修改
/deleteProducts/20    # 刪除
```

而在 RESTful API 中則會是這樣：

```
GET /products/20        # 查詢
PUT /products/20        # 修改
DELETE /products/20     # 刪除
```

