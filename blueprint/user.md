# Group user

## ユーザーエンドポイント [/user]

### 新規ユーザー作成 [POST]

+ Request (application/json)
    + Attributes
        + userid: test_user_id (string, required) - 登録するユーザーID
        + name: テストユーザー (string, required) - 登録する名前
        + password: test_user_pass (string, required) - 登録するパスワード
        + mobile: 09012345678 (string, required) - SMS用の電話番号

+ Response 200 (application/json)
    + Attributes
        + token: valid_access_token (string) - アクセストークン
        + name: テストユーザー (string) - ユーザー名

+ Response 400 (application/json)
    + Attributes
        + message: user post is faild (string) - 登録処理に失敗（ユーザ名の重複など）


## ユーザに関する操作エンドポイント [/user/{userId}]

+ Parameters
    + userId: taro1234 (string) - 操作したいユーザID

### ユーザ設定情報の取得 [GET]
ユーザのプロファイル情報を取得する。他人の情報もとれる

+ Request
    + Headers
        Authorization : Bearer valid_access_token

+ Response 200 (application/json)
    + Attributes
        + userid: test_user_id (string, required) - 登録するユーザーID
        + name: テストユーザー (string) - ログインユーザーの名前

+ Response 401 (application/json)
    + Attributes
        + message: invalid token (string) - トークンの認証に失敗


### パスワード/名前の変更 [PUT]

+ Request (application/json)
    + Headers
        Authorization : Bearer valid_access_token
    + Attributes
        + newPassword: test_user_new_pass (string) - 新しいパスワード
        + name: 新テストユーザー (string) - 新しい名前
        + mobile: 09012345678 (string) - SMS用の電話番号

+ Response 200 (application/json)
    + Attributes
        + newPassword: test_user_new_pass (string) - 新しいパスワード
        + name: 新テストユーザー (string) - 新しい名前

+ Response 401 (application/json)
    + Attributes
        + message: invalid token (string) - トークンの認証に失敗

        
### ユーザー削除 [DELETE]
自分を削除する
+ Request (application/json)
    + Headers
        Authorization : Bearer valid_access_token

+ Response 200 (application/json)
    + Attributes
        + message: ok (string) - ユーザ削除完了



## ユーザ毎位置情報エンドポイント [/user/{userId}/position]

+ Parameters
    + userId: taro1234 (string) - 操作したいユーザID

### 最新位置情報取得 [GET]
最新の位置情報を取得する。

+ Request (application/json)
    + Headers
        Authorization : Bearer valid_access_token

+ Response 200 (application/json)
    + Body
        [
            {"userid": "userid123", "position": { "lat": 35.123, "lon" : 48.111 } "lastUpdate": "2017-03-31 15:30:31", "name":"田中" }
        ]

+ Response 204 (application/json)
    + Attributes
        + message: no history (string) - 位置情報一個もない

+ Response 404 (application/json)
    + Attributes
        + message: no useruser  (string) - そんなユーザはいないです


### 最新位置情報更新 [POST]

+ Request (application/json)
    + Headers
        Authorization : Bearer valid_access_token
    + Attributes
        + position: { "lat": 35.123, "lon" : 48.111 }  (string, required) - 登録する位置情報

+ Response 200 (application/json)
    + Attributes
        + position: { "lat": 35.123, "lon" : 48.111 }  (string, required) - 登録した位置情報をおうむ返し

+ Response 400 (application/json)
    + Attributes
        + message: user post is faild (string) - 登録処理に失敗（認証エラーなど）
