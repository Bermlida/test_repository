# Subresources

---

一般而言，每個 URI 都會對應到每個不同類型的資源，而這些 URI 也因此對應著相應類型資源的集合。

然而，有些資源會與其他資源存在著密切的關係，可能依賴其他資源或者包含其他資源，

為了表示這樣的關係，則可以使用子資源的架構來表示。

這樣的情形通常有兩種狀況：

* 資源本身包含了其他資源的集合

* 資源本身包含的其他資源僅僅一項或一個。


## 範例

* 假設一個網站存在著許多用戶，每個用戶都擁有一台以上的車輛，

  因此是「資源本身包含了其他資源的集合」，

  取得用戶識別碼為 25 的用戶所擁有的車輛可以如下所示：

  ```
  GET /users/25/cars/
  ```

  取得用戶識別碼為 25 的用戶所擁有的，車輛識別碼為 20 的車輛可以如下所示：

  ```
  GET /users/25/cars/20
  ```

* 假設一個網站存在著許多用戶，每個用戶的個人資料都只會有一項或一個，

  因此是「資源本身包含的其他資源僅僅一項或一個」，

  取得用戶識別碼為 25 的用戶的個人資料可以如下所示：

  ```
  GET /users/25/profile
  ```

