# Constraints

---

**REST** 在概念上提出了幾項  **條件\/原則\(Constraints\)**，

當我們的設計系統符合這些 **條件\/原則\(Constraints\)** 的時候，我們可稱這個系統為 **RESTful**。

**REST** 提及的 **條件\/原則\(Constraints\)** 如下：

* **客戶-伺服器\(Client-Server\)**：使用主從式架構設計，表現為請求 - 回應的形式。
* **無狀態\(Stateless\)**：客戶端與服務端的通訊不需依賴狀態，從客戶端發出的各項請求必須包含該次請求所需的所有資訊，而不需依賴其他請求的狀態。
* **可實作緩存機制\(Cacheable\)：**可以在客戶端或服務端中實作**緩存\(Cache\)**機制，以部分或完全的節省服務端及客戶端兩者間的通訊次數，並提高效率。
* **一致性的操作界面\(Uniform Interface\)**：在 Components \(後面會介紹 REST Components\) 之間使用一致性的操作介面，為了透過介面降低耦合並提高獨立性 \(Independent\)。其中 REST 對 Interface 定義了四種限制（目前我認為 Uniform Interface 就是 REST 的核心價值，有效的藉由抽象介面來隔離實作細節）
* **層次化的系統\(Layered System\)**：可分層的系統架構，目的在於隱藏介面後的實作細節，使得系統更容易實現快取、加密等等機制。
* **所需代碼\(Code-On-Demand\)**：可執行程式碼的設計， 服務端可暫時延伸或自訂功能把一些運算邏輯轉移到客戶端執行，可透過如 **Java applets** 或 **client-side script **\(如 **JavaScript **\) 的技術來實現。（非必要實作項目）

