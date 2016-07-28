# List All User

列出所有使用者

## 路徑

```
GET /users
```

## 參數

無

## 範例

### 請求

```
$ curl -X GET http://laravel.framework/users
```

### 回應

```
{
  "flag": true,
  "data": [
    {
      "id": 20,
      "name": "YhhhhhhhSSSSSSSSSSSSSSS",
      "email": "email@email5.email",
      "created_at": "2016-07-15 08:43:48",
      "updated_at": "2016-07-15 08:55:35"
    },
    {
      "id": 21,
      "name": "form, update",
      "email": "from@ann",
      "created_at": "2016-07-18 02:20:50",
      "updated_at": "2016-07-18 02:22:23"
    },
    {
      "id": 22,
      "name": "name22",
      "email": "create@from",
      "created_at": "2016-07-18 02:25:32",
      "updated_at": "2016-07-18 02:26:03"
    },
    {
      "id": 23,
      "name": "name23",
      "email": "name221@name221.name221",
      "created_at": "2016-07-18 08:40:51",
      "updated_at": "2016-07-18 08:41:31"
    },
    {
      "id": 24,
      "name": "name321",
      "email": "three@two.one000",
      "created_at": "2016-07-18 09:59:54",
      "updated_at": "2016-07-18 10:01:48"
    },
    {
      "id": 25,
      "name": "namename",
      "email": "email@emailemail.email",
      "created_at": "2016-07-19 06:24:06",
      "updated_at": "2016-07-19 06:24:06"
    }
  ]
}
```

