# Architectural Elements

---

在REST的架構中， 定義了三種角色，分別是 **Data Elements, Connectors **與** Components**。 

### **Data Elements**

Data Elements 主要的概念為 Resources，在 REST 的系統架構中所有的 Entity \(實體\) 使用全域唯一的 Resource Identifiers 進行識別與定義（全域的目的為盡可能讓這樣的識別資源方法在不同系統中能夠正確地指向唯一的實體），並且有效地將實體資源與 Resource Identifiers 進行 mapping。資源存取者透過 Connectors 操作資源，然而很重要的一件事，這樣資源的識別命名方式能夠直覺與合理是最好不過的。 

**Representations - **在 REST 的概念中 Components 之前是透過 Representations 來表示這個資源目前的狀態，Representations 就像我們所熟悉的 Content-Type。假設我們取得某個人在某個網站當前的照片，_**image\/jpg**_ 這樣的 Content-Type 就是一種 Representations; 當然我們也可以取得這個人在這個網站當前的個人基本資料，或許 Content-Type 會使用 _application_**\/**_xml_ \(又是另一種Representations\)。Client \(User Agent\) 在實作上會依據 Representations \(就是Content-Type\) 來正確地 Render 訊息，這樣的行為是不是很像我們在使用的瀏覽器呢？ 

