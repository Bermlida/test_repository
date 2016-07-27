# Architectural Elements

---

在 **REST **的架構中， 定義了三種角色，分別是 **Data Elements, **連接器\(Connectors\)** **與** 組件\(Components\)**。

### **Data Elements**

Data Elements 主要的概念為 **資源\(Resources\)** 與 **資源表述\(Representations\)** 。

在 **REST** 的系統架構中，所有的 **實體\(Entity\)** 即為 **資源\(Resources\)**，使用全域且唯一的 **資源標識符\(Resource Identifier\)** 進行識別與定義（設定為全域的目的是盡可能讓這樣的識別資源方法在不同系統中能夠正確地指向唯一的實體），並且有效地將資源與資源標識符進行對應，資源標識符的識別命名應當是直覺且合理的，以利 Components 透過 Connectors 進行操作。

**資源表述\(Representations\)** 用來表示這個資源目前的狀態，為資源的表達形式，假設我們取得某位用戶的資料，可以使用 **Xml\(**`application/xml`**\)**，也可以使用 **Json\(**`application/json`**\)**_，_這兩者是兩種不同的表達形式。

**Client**\(**User Agent**\) 在實作上會依據表達形式來正確地 **渲染\(Render\)** 訊息。

### **連接器**

連接器是組件之間進行溝通的介面，透過不同型態的連接器，組件之間相應有著不同的溝通模式，

包含了以下五種型態：

* **Client**：libwww, libwww-perl
* **Server**：libwww, Apache API, NSAPI
* **Cache**：browser cache, Akamai cache network
* **Resolver**：bind \(DNS lookup library\)
* **Tunnel**：SOCKS, SSL after HTTP CONNECT

**Client **通過發送 **請求\(Request\)** 來發起通訊；

**Server** 監聽通訊，並對 **Client** 所發出的請求送出 **回應\(Response\)**；

**Cache** 則實作在 **Client** 或 **Server** 中，針對實際的需要進行緩存；

**Resolver** 能夠在 **Client** 與 **Server** 的通訊上正確的進行解析處理；

**Tunnel** 可以強制進行加密等等的工作。

### **組件**

組件是整個通訊過程中的，依其行為的不同，扮演不同角色的模組。

其中，根據行為的不同，包含以下四種角色類型：

* **User Agent** ： Netscape Navigator, Lynx, MOMspider
* **Origin Server** ： Apache httpd, Microsoft IIS
* **Gateway** ： Squid, CGI, Reverse Proxy
* **Proxy** ： CERN Proxy, Netscape Proxy, Gauntlet

**User Agent** 使用 **Client Connector** 對 **Server** 進行連線，並且實作如何正確地渲染來自於 **Server** 的 **Response** 。

**Origin Server** 透過 **Server Connector** 並且提供一個通用的 **介面\(Interface\)** 來接收 **Request**，透過介面隱藏資源的實作細節。

而 **Gateway** 與 **Proxy** 能夠在 **Client** 與 **Server** 通訊的過程中增加效率與安全性。

