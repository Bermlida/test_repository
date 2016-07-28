# Delete User

刪除使用者

## 定義

```
DELETE /users/{user_id}
```

## 參數

無

## 範例

### 請求：

```
$ curl -X DELETE http://laravel.framework/users/26
```

### 回應：

```
{
    "flag": true,
    "message": "user delete"
}
```

