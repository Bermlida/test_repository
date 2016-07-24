# Architectural Elements

---

在REST的架構中， 定義了三種角色，分別是 **Data Elements, Connectors **與** Components**。

### **Data Elements**

Data Elements 主要的概念為 資源\(Resources\) 與其 表述形式\(**Representations\)** ，

在 REST 的系統架構中，所有的 實體\(Entity\) 即為 資源\(Resources\)，使用全域且唯一的 **資源標識符\(Resource Identifier\)** 進行識別與定義（全域的目的為盡可能讓這樣的識別資源方法在不同系統中能夠正確地指向唯一的實體），並且有效地將 資源\(Resources\) 與 **資源標識符\(Resource Identifier\)** 進行對應。

在 REST 的概念中，Components 之前是透過  表述形式\(**Representations\)**  來表示這個資源目前的狀態， 表述形式\(**Representations\)**  就像我們所熟悉的 Content-Type。假設我們取得某位用戶的資料，或許 Content-Type 會使用 _application\/xml_ ，也或許會使用 _application\/json_，因此這兩者是兩種不同的 表述形式\(**Representations\)** 。

Client \(User Agent\) 在實作上會依據  表述形式\(**Representations\)**  \(就是Content-Type\) 來正確地 Render 訊息。

### **Connectors**

Connectors 包含了以下五種型態：

* **Client **- libwww, libwww-perl
* **Server **- libwww, Apache API, NSAPI
* **Cache **- browser cache, Akamai cache network
* **Resolver **- bind \(DNS lookup library\)
* **Tunnel **- SOCKS, SSL after HTTP CONNECT

  資源存取者透過 Connectors 操作資源，然而很重要的一件事，這樣資源的識別命名方式能夠直覺與合理是最好不過的。


這 些 Connectors 透過抽象的介面與 Components 進行溝通，在 REST 中所使用的連線都必須是 Stateless \(無狀態\)。Connectors 主要的形態為 Client 與 Server，由 Server 監聽 Client 所發出的 Request 並且回應 Response（連線機制與HTTP完全相符）。然而 Cache 的機制可以實作在 Client 或 Server 中（像是 Browser 與 Server 的 Cache 機制）；Resolver 能夠在 Client 與 Server 的溝通上正確的進行解析處理；Tunnel 可以強制進行加密等等的工作。有趣的是這些功能都是獨立的，對於操作者來說都是隱藏且不可見的。

### Components

Components 包含以下四種角色

* **User Agent** - Netscape Navigator, Lynx, MOMspider
* **Origin Server** - Apache httpd, Microsoft IIS
* **Gateway **- Squid, CGI, Reverse Proxy
* **Proxy **- CERN Proxy, Netscape Proxy, Gauntlet

User Agent 使用 Client Connector 對 Server 進行連線（User Agent 就像是瀏覽器），並且實作如何正確地 Render 來至於 Server 的 Response。Origin Server 透過 Server Connector 並且提供一個通用的 Interface 來接收 Request，透過 Interface 隱藏 Resource 的實作細節。就像我們使用 Browser 瀏覽網站的時候，不需要知道網站是用什麼樣的技術實現的。而 Gateway 與 Proxy 能夠在 Client 與 Server 溝通的過程中增加效率與安全性。

