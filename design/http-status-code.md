# **HTTP Status Code**

---

**HTTP 狀態碼 \(HTTP Status Code\)** 是用來表示網頁伺服器 HTTP 回應狀態的 3 位數字代碼，

當服務端送出回應訊息給客戶端時，這些數字代碼可以幫助客戶端依據不同的回應狀態進行相對應的處理。

## 數字類型及狀態對應

所有狀態碼的第一個數字代表了回應的五種狀態之一，這五種狀態及對應的數字如下所示：

| 數字類型 | 回應狀態 | 說明 |
| :--- | :--- | :--- |
| 1xx | 訊息 | 請求已被接受，需要繼續處理 |
| 2xx | 成功 | 請求已成功被伺服器接收、理解、並接受。 |
| 3xx | 重新導向 | 需要用戶端採取進一步的操作才能完成請求。通常，這些狀態碼用來重新導向 |
| 4xx | 用戶端錯誤 | 用戶端看起來可能發生了錯誤，妨礙了伺服器的處理 |
| 5xx | 伺服器錯誤 | 伺服器在處理請求的過程中有錯誤或者異常狀態發生，也有可能是伺服器意識到以當前的軟硬體資源無法完成對請求的處理 |

## 常用清單

以下列出了，在設計 RESTful API 時，常用的狀態代碼清單：

* `200 OK` ：成功執行 GET、PUT、PATCH 或 DELETE 時使用，也可用於當 POST 不是新增資源的操作行為。
* `201 Created` ：使用 POST 並成功建立資源時回應此狀態碼，同時在標頭以 location 欄位提供定位至新資源的 URI 。
* 204 No Content - Response to a successful request that won't be returning a body \(like a DELETE request\)
* 304 Not Modified - Used when HTTP caching headers are in play
* 400 Bad Request - The request is malformed, such as if the body does not parse
* 401 Unauthorized - When no or invalid authentication details are provided. Also useful to trigger an auth popup if the API is used from a browser
* 403 Forbidden - When authentication succeeded but authenticated user doesn't have access to the resource
* 404 Not Found - When a non-existent resource is requested
* 405 Method Not Allowed - When an HTTP method is being requested that isn't allowed for the authenticated user
* 410 Gone - Indicates that the resource at this end point is no longer available. Useful as a blanket response for old API versions
* 415 Unsupported Media Type - If incorrect content type was provided as part of the request
* 422 Unprocessable Entity - Used for validation errors
* 429 Too Many Requests - When a request is rejected due to rate limiting

