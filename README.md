# openapi-prism1

OpenAPI の mock サーバとして有名な [prism](https://github.com/stoplightio/prism) を使う練習。

## 環境 (2023-06現在)

- Node.js (18.16.0)
- pnpm (8.6.2)

## このプロジェクトを生成した手順

```bash
mkdir prism1
cd prism1
pnpm init
pnpm i -D @stoplight/prism-cli
```

次に、`./openapi.yaml` を書く。
もちろんexportしたやつを置いてもいいし、http経由でもいい(らしい)。

最後に、`./package.json` の `scripts` に

```json
  "scripts": {
    ...
    "mock": "prism mock ./openapi.yaml",
    ...
  },
```

の1行を追加。

## 動かし方

Node.jsのプロジェクトなので、`git clone`したら最初に1回

```bash
pnpm i
```

以後は

```bash
pnpm mock
```

で起動。デフォルトでは <http://127.0.0.1:4010> で上がる。  
別のポートで立ち上げたいときは `-p` オプション (`prism mock --help` 参照)

で、本プロジェクト添付の例では

```bash
curl http://127.0.0.1:4010/api/v1/hello
```

で "hello" と帰ってきたらとりあえずOK。

## メモ

ホットリロードが効いてる。
このレポジトリの場合 `./openapi.yaml` を編集すると
prismサーバがリロードされる。

## TODO

CORSはどうなってるか調べる。
[CORS | Prism](https://docs.stoplight.io/docs/prism/5ee9bb8a1cf2b-cors) によると `*` らしい。

## 参考

- [Swagger Editor](https://editor.swagger.io/)
