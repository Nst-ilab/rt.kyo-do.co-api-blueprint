# rt.kyodo.co-api-blueprint

[rt.kyodo.co](https://rt.kyo-do.co/)のバックエンドの[api blueprint](https://apiblueprint.org/)です。

## セットアップ

```bash
$ npm install
```

## コマンド(npm-scripts)

### APIドキュメントを作成する

```bash
$ npm run docs
#->docs/index.htmlとしてAPIドキュメントが作成される
```

#### 展開先(GitHub Page)
https://nst-ilab.github.io/rt.kyo-do.co-api-blueprint/

### APIドキュメントをプレビューする

```bash
$ npm run docs-server
#->http://localhost:3030へアクセスするとAPIドキュメントを参照できる
# 中止する際はctrl+c
```

### APIモックを起動させる

```bash
$ npm run mock
#->http://localhost:3000にAPIモックが展開される
# 停止する際はctrl+c
```
