# Update User

更新使用者

## 路徑

```
/users/{user_id}
```

## 參數

### Request Body

| 參數名稱 | 類型 | 是否必選 | 描述 |
| :--- | :--- | :--- | :--- |
| name | string | 否 | 使用者名稱 |
| email | string | 否 | 使用者 email |
| password | string | 否 | 使用者密碼 |

## 範例

### 請求

```
$ curl -X PUT http://laravel.framework/users/25 --data '
{
  "name": "name65536"
}'
```

### 回應

```
{
    "flag": true, 
    "data": {
        "id": 25, 
        "name": "name65536", 
        "email": "email@emailemail.email", 
        "created_at": "2016-07-19 06:24:06", 
        "updated_at": "2016-07-28 00:49:47"
    }
}
```

