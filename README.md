# hello-world-http

このプロジェクトは [cloudflare/workers-rs](https://github.com/cloudflare/workers-rs) を参考にした、Rust製Cloudflare Workers用の最小構成HTTPサーバサンプルです。

## 概要

RustでCloudflare Workers向けにHTTPリクエストを受け付け、空のHTTP 200レスポンスを返すシンプルなサーバです。

## ディレクトリ構成

```
.
├── Cargo.toml
├── Cargo.lock
├── wrangler.toml
├── src/
│   └── lib.rs
├── build/
│   └── worker/
│       ├── shim.mjs
│       └── index.wasm
├── .gitignore
└── node_modules/
```

## 主なファイル

- `src/lib.rs`  
  Rustのエントリーポイント。HTTPリクエストを受けて200 OKの空レスポンスを返します。

- `wrangler.toml`  
  Cloudflare Workersのデプロイ設定ファイル。`cargo install -q worker-build && worker-build --release` でビルドします。

- `build/worker/shim.mjs`  
  Cloudflare Workersで動作するためのJSシム。RustでビルドしたWASMをラップします。

- `build/worker/index.wasm`  
  RustコードをWASMにビルドした成果物。

## ビルド・デプロイ方法

1. 依存パッケージのインストール  
   ```
   npm install
   ```

2. ビルド  
   ```
   npx wrangler build
   ```
   または  
   ```
   cargo install -q worker-build
   worker-build --release
   ```

3. ローカルでのテスト  
   ```
   npx wrangler dev
   ```

4. デプロイ  
   ```
   npx wrangler deploy
   ```

---

本プロジェクトは [cloudflare/workers-rs](https://github.com/cloudflare/workers-rs) のドキュメント・サンプルを参考にしています。 