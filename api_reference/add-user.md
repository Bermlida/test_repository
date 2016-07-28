# Add User

新增使用者

## 路徑

```
POST /users
```

## 參數

### Request Body

| 參數名稱 | 類型 | 是否必選 | 描述 |
| :--- | :--- | :--- | :--- |
| name | string | 是 | 使用者名稱 |
| email | string | 是 | 使用者 email |
| password | string | 是 | 使用者密碼 |

## 範例

### 請求

```
$ curl -X POST http://laravel.framework/users --data '
{
    "name": "name556",
    "email": "email@email456.email",
    "password": "1234567890",
}'
```

### 回應

```
{
    "flag": true,
    "data": {
        "name": "name556",
        "email": "email@email456.email",
        "updated_at": "2016-07-27 10:04:53",
        "created_at": "2016-07-27 10:04:53",
        "id": 26
    }
}
```

