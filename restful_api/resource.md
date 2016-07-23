# Resource

在 REST 中的 **資源 \(Resource\)** 代表整個網路上的資源。

網路上提供了各式各樣的資源，而這些資源由 **統一資源標識符 \(URI, Uniform Resource Identifier\)**  來表示 。 

**URI** 由 **Prefix** + **API endpoint **組成。

**Prefix **的部份可有可無，例如 \/api 或 \/api\/v1。

針對** API endpoint **的設計，具備下列重要原則：
1. 一般資源用複數名詞，例如\/books或\/books\/123；複數可以保持API endpoint的一致性，所以一般資源建議用複數。
2. 唯一資源（亦即對client而言只有一份的資源）用單數名詞
3. 資源的層級架構，可以適當反應在 **API endpoint** 設計上，例如 \/books\/123\/chapters\/2。
      Utility API與resource API性質不同，它的endpoint設計只要合理即可，例如\/search?q={keywords}。
      建議URI components都用小寫，兩個字之間用減號-或底線\_隔開皆可，但應保持一致。（我個人偏好用-）


