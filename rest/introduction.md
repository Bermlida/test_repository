# Introduction

---

**具象狀態傳輸** \( **Representational State Transfer**，簡稱 **REST** \)，

是一種軟體架構風格，其目的是構建可擴展的 Web Service** **。

## 定義

從 **資源\(Resource\) **的角度來觀察整個網路，分布在網路各處的資源以 **資源標識符\(Resource Identifier\)** 表示，而應用程序通過資源標識符來進行對資源的操作，並獲得其 **表述\(Representational\) **。

獲得這些表述致使這些應用程序根據資源的表現形式決定如何 **轉移\(Transfer\) **其自身應用 **狀態\(State\)** 。

隨著不斷獲取資源的表述，應用程序不斷地在轉變著其狀態，就是所謂的 **具象狀態傳輸\(Representational State Transfer\) **。

## REST Triangle

綜上所述，根據 REST 的定義，可以得到三個關鍵概念，

這三個關鍵概念構成了一個三角形，言簡意賅的圖解了 REST** **的架構與運作方式，如下圖所示：

![](http://www.onlamp.com/2008/02/19/graphics/RESTful-Triangle.png)

這個三角形的三個角，個別對應了以下三個概念：

1. **nouns**：名詞，用來識別資源的名稱，對應到不同內容的資源，使用這些名詞進行對資源的操作。
2. **verbs**： 動詞，對資源進行的操作行為，使用這些動詞具體指定對資源的操作行為。
3. **content types**：內容型態，資源的表述\(或稱作表現形式\)，指定不同的內容型態，讓相同的資源內容以不同的格式呈現。

