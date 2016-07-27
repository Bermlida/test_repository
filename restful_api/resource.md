# Resource

---

### 定義

在 **REST **的架構中， **nouns** ，指的是名詞，

指的是 **資源標識符\(Resource Identifier\)**，用來識別資源的名稱 。

定義各種各樣不同形式的名稱，以對應整個網路上的各式各樣不同的資源。

而在 **RESTful API** 中，**REST **架構中的 **Nouns** ，

對應於此指的是以 **統一資源標識符\( Uniform Resource Identifier**，簡稱 **URI \)**  來表示的各種不同的網路資源。

### **統一資源標識符**

**統一資源標識符\(URI\)** 是一個用於標識某項網路資源，定義其名稱的字串。

**URI** 結構如下：

```
[scheme:][//host][/][path][?query][#fragment]
```

`[scheme:]`：指定了 **URI** 採用的協定內容，其語法及語義。

`[//host]` 及 `[/]`：前者指定網域名稱或 **IP** 位址，後者分用來與路徑分隔。

`[path]`：路徑，透過不同的路徑設計對應不同的資源。

`[?query]`：傳遞至指定路徑的參數。

`[#fragment]`：提供導向至次要資源的標識符，像是網頁中的錨點之類的。

### 範例

以一個簡單的網路商務應用為例：

列舉所有商品

```
http://www.example.com/products
```

呈現某一件商品

```
http://www.example.com/products/23458963
```

