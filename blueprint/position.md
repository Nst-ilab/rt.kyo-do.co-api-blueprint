# Group position

## 全ユーザの位置情報 [/position/all]

### 全登録ユーザの最新位置情報を取得 [GET]

+ Request (application/json)
    + Headers
        Authorization : Bearer valid_access_token

+ Response 200 (application/json)
     + Body
        [
            {"userId": "userid123", "position": { "lat": 35.123, "lng" : 48.111 } "lastUpdate": "2017-03-31 15:30:31", "name":"田中" },
            {"userId": "userid345", "position": { "lat": 35.112, "lng" : 48.111 } "lastUpdate": "2018-01-31 15:30:31", "name":"鈴木" },
        ]

+ Response 401 (application/json)
    + Attributes
        + message: invalid token (string) - トークンの認証に失敗


+ Response 400 (application/json)
    + Attributes
        + message: user post is faild (string) - 送信パラメータの不正


