# Resource

### 定義

---

在 **REST **的架構中， **nouns** 是名詞，

指的是 **資源標識符\(Resource Identifier\)**，用來識別資源的名稱 。

定義各種各樣不同型式的名稱，以對應整個網路上的各式各樣不同的資源。

而在 **RESTful API** 中，**REST **架構中的 **Nouns** ，

對應於此指的是以 **統一資源標識符\( Uniform Resource Identifier**，簡稱 **URI \)**  來表示的各種不同的網路資源。

### **統一資源標識符**

---

**統一資源標識符\(URI\)** 是一個用於標識某項網路資源，定義其名稱的字串。

**URI** 由 **Prefix** + **API endpoint **組成。

**Prefix **的部份可有可無，例如 `/api` 或 `/api/v1`。

針對** API endpoint **的設計，具備下列重要原則：
1. 一般資源用複數名詞，例如 `/books` 或 `/books/123` ；複數可以保持 **API endpoint **的一致性，所以一般資源建議用複數。
2. 唯一資源（亦即對 **客戶端 **而言只有一份的資源）用單數名詞
3. 資源的層級架構，可以適當反應在 **API endpoint** 設計上，例如 `/books/123/chapters/2`

建議 **URI** 都用小寫表示，兩個單字之間用**減號 \(dash\)  -  **或** 底線\(underline\) \_ **隔開皆可，但應保持一致。

### 範例

---

以一個簡單的網路商務應用為例：

列舉所有商品

```
http://www.example.com/products
```

呈現某一件商品

```
http://www.example.com/products/23458963
```

