# Architectural Elements

---

在 **REST **的架構中， 定義了三種角色，分別是 **Data Elements, Connectors **與** Components**。

### **Data Elements**

Data Elements 主要的概念為 **資源\(Resources\)** 與 **資源表述\(Representations\)** 。

在 **REST** 的系統架構中，所有的 **實體\(Entity\)** 即為 **資源\(Resources\)**，使用全域且唯一的 **資源標識符\(Resource Identifier\)** 進行識別與定義（設定為全域的目的是盡可能讓這樣的識別資源方法在不同系統中能夠正確地指向唯一的實體），並且有效地將資源與資源標識符進行對應，資源標識符的識別命名應當是直覺且合理的，以利 Components 透過 Connectors 進行操作。

**資源表述\(Representations\)** 用來表示這個資源目前的狀態，為資源的表達形式，假設我們取得某位用戶的資料，可以使用 **Xml\(**_`application/xml`_**\)**，也可以使用 **Json\(**_`application/json`_**\)**_，_這兩者是兩種不同的表達形式。

**Client**\(**User Agent**\) 在實作上會依據表達形式來正確地 **渲染\(Render\)** 訊息。

### **Connectors**

Connectors 包含了以下五種型態：

* **Client**：libwww, libwww-perl
* **Server**：libwww, Apache API, NSAPI
* **Cache**：browser cache, Akamai cache network
* **Resolver**：bind \(DNS lookup library\)
* **Tunnel**：SOCKS, SSL after HTTP CONNECT

Connectors 透過抽象的介面與 Components 進行溝通，在 **REST** 中所使用的連線都必須是 **Stateless\(無狀態\)** 的。

Connectors 主要的運作形式為 **Client** 與 **Server**，由 **Server** 監聽 **Client** 所發出的 **Request** 並且回應 **Response**；

**Cache** 則實作在 **Client** 或 **Server** 中，針對實際的需要進行緩存；

**Resolver** 能夠在 **Client** 與 **Server** 的通訊上正確的進行解析處理；

**Tunnel** 可以強制進行加密等等的工作。

這些功能都是獨立的，但對於操作者來說都是隱藏且不可見的。

### Components

Components 包含以下四種角色

* **User Agent** ： Netscape Navigator, Lynx, MOMspider
* **Origin Server** ： Apache httpd, Microsoft IIS
* **Gateway** ： Squid, CGI, Reverse Proxy
* **Proxy** ： CERN Proxy, Netscape Proxy, Gauntlet

**User Agent** 使用 **Client Connector** 對 **Server** 進行連線，並且實作如何正確地渲染來自於 **Server** 的 **Response** 。

**Origin Server** 透過 **Server Connector** 並且提供一個通用的 **介面\(Interface\)** 來接收 **Request**，透過介面隱藏資源的實作細節。

而 **Gateway** 與 **Proxy** 能夠在 **Client** 與 **Server** 通訊的過程中增加效率與安全性。

