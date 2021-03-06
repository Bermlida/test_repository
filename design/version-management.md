# Version Management

---

隨著服務端系統逐漸發展，新的特性、新的資源逐漸被添加到該系統中，

在這過程中，對外開放的 URI 、操作方法、回應格式及狀態碼，必須因應客戶端的狀況而向後兼容。

然而，當原有的 API 設計很難兼容現有資源應有的定義時，就需要考慮是否應該提供一個新版本的 API，

這時 API 的版本管理就成為了重點。

一般而言，API 的版本資訊可以包含於 URI 之中，也可以置於標頭欄位，又或者是兩者兼用。

## 範例

假設現在 API 的版本有三個不同的版本，

則客戶端可藉由以下方式指定 API 的版本，以選擇使用所需的 API：

* ### URL

  倘若 API 的版本資訊包含於 URI 之中，則可以透過 URI 指定版本號，選擇使用的 API 版本，如下所示：

  ```
    GET /api/v1/users/25    # 使用第一版的 API，取得用戶識別碼為 25 的用戶資料

    GET /api/v2/users/25    # 使用第二版的 API，取得用戶識別碼為 25 的用戶資料
  ```

  另外，也可以指定一個通用的 API 介面，讓客戶端透過這個介面使用最新版本的 API：

  ```
    GET /api/users/25    # 使用最新版 API，取得用戶識別碼為 25 的用戶資料
  ```

* ### Headers

  倘若 API 的版本資訊須置於標頭欄位，才能指定並使用特定版本的 API，則如下所示：

  假設客戶端打算使用第二版的 API，並取得用戶識別碼為 25 的用戶資料

  * 請求：

    ```
      GET /api/users/25
      Host: laravel.framework
      Authorization: Basic xxxxxxxxxxxxxxxxxxx
      Accept: application/vnd.laravel.framework-v2+json
    ```

  * 回應：

    ```
    HTTP/1.1 200 OK
    Content-Type: application/vnd.laravel.framework-v2+json
    Content-Length: xxx

    {
       "uri": "/api/users/25",
       "name": "name23456",
       ......
    }
    ```



