# Constraints

---

**REST** 在概念上提出了幾項  **條件\/原則\(Constraints\)**，

當我們的設計系統符合這些條件\/原則的時候，我們可稱這個系統為 **RESTful**。

**REST** 提及的條件\/原則如下：

* **客戶-伺服器\(Client-Server\)**：使用主從式架構設計，表現為 **請求\(Request\)** - **回應\(Response\) **的形式。
* **無狀態\(Stateless\)**：客戶端與服務端的通訊不需依賴狀態，從客戶端發出的各項請求必須包含該次請求所需的所有資訊，而不需依賴其他請求的狀態。 
* **可實作緩存機制\(Cacheable\)：**可以在客戶端或服務端中實作 **緩存\(Cache\) **機制，以部分或完全的節省服務端及客戶端兩者間的通訊次數，並提高效率。
* **一致性的操作界面\(Uniform Interface\)**：在 **Components** 之間使用 **一致性的操作介面\(Uniform Interface\)** ，透過 **介面\(Interface\)** 降低 **耦合\(Coupling\) **並提高 **獨立性\(Independent\)。**
  這項條件\/原則下又分為下列各項子條件\/原則：
  * Identification of resources 資源識別，資源的表述方式和資源的實際形態分離，比如用XML或者JSON來表述資源而服務器內部可能用數據庫來存儲資源Manipulation of resources through these representations 資源包含足夠的元數據來操作資源Self-descriptive messages 每條消息都包含足夠的元信息來表述自己如何被消費Hypermedia as the engine of application state \(HATEOAS\) 這個有點複雜！ ！



* **層次化的系統\(Layered System\)**：可分層的系統架構，目的在於隱藏介面後的實作細節，使得系統更容易實現快取、加密等等機制。
* **所需代碼\(Code-On-Demand\)**：可執行程式碼的設計， 服務端可暫時延伸或自訂功能把一些運算邏輯轉移到客戶端執行，可透過如 **Java applets** 或 **client-side script **\(如 **JavaScript **\) 的技術來實現。（非必要實作項目）

