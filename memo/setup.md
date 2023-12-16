## 手順 (macOS)
### Node.js
```bash
# nvsインストール
export NVS_HOME="$HOME/.nvs"
git clone https://github.com/jasongin/nvs "$NVS_HOME"
. "$NVS_HOME/nvs.sh" install
nvs --version # check

# Node.jsインストール
nvs add 20.10.0
nvs use 20.10.0
node --version # check
```

### React project
```bash
# React単品はフレームワークの利用がおすすめらしいのでそうする (Next.js)
# https://ja.react.dev/learn/start-a-new-react-project
## next.js 公式ドキュメント
## https://nextjs.org/docs/getting-started/installation#manual-installation

cd src/nextjs
# -- package.json追加
vi package.json
#    /src/nextjs/package.json
# {
#   "scripts": {
#     "dev": "next dev",
#     "build": "next build",
#     "start": "next start",
#     "lint": "next lint"
#   }
# }

# パッケージインストール
# ※node_modulesのgitignore追加忘れずに！
npm install next@latest react@latest react-dom@latest

```

### Next.jsチュートリアルメモ
* Next.jsのルーティングはディレクトリ構造に依存する
  - まずは`/app`を切る
  - `/app`配下に`layout.tsx`と`page.tsx`を作る (この機会にTS覚えよう)
* `layout.tsx`にコンポーネント実装
```ts
export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  )
}
```
* `page.tsx`にコンポーネント実装
```ts
export default function Page() {
  return <h1>Hello, Next.js!</h1>
}
```

* `/pages`ディレクトリを切って色々追加 (略)
* ローカルサーバー起動
```bash
cd /react-toy/src/nextjs
npm run dev

# Run npm run dev to start the development server.
# Visit http://localhost:3000 to view your application.
# Edit app/page.tsx (or pages/index.tsx) file and save it to see the updated result in your browser.
```

* エラーになった(´・ω・`)
```
$ npm run dev

> @ dev /Users/user/Projects/react-toy/src/nextjs
> next dev

/Users/user/Projects/react-toy/src/nextjs/node_modules/next/dist/lib/picocolors.js:134
const { env, stdout } = ((_globalThis = globalThis) == null ? void 0 : _globalThis.process) ?? {};
                                                                                             ^

SyntaxError: Unexpected token ?
    at Module._compile (internal/modules/cjs/loader.js:872:18)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:947:10)
    at Module.load (internal/modules/cjs/loader.js:790:32)
    at Function.Module._load (internal/modules/cjs/loader.js:703:12)
    at Module.require (internal/modules/cjs/loader.js:830:19)
    at Module.mod.require (/Users/user/Projects/react-toy/src/nextjs/node_modules/next/dist/server/require-hook.js:65:28)
    at require (internal/modules/cjs/helpers.js:68:18)
    at Object.<anonymous> (/Users/user/Projects/react-toy/src/nextjs/node_modules/next/dist/build/output/log.js:55:21)
    at Module._compile (internal/modules/cjs/loader.js:936:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:947:10)
```
  - 構文エラーだからTypeScript入れてないのが原因かな？
    - `$ npm install typescript`
    - だめぽ

* プロジェクト作成コマンドはちゃんとある様子。なのでこっち使う
https://qiita.com/itachi/items/05fbe67c7168703a34e7
`$ npx create-next-app sample --ts`

* こっちもエラーになった、、、
```
Cannot find module 'fs/promises'
```
  - nodejsのバージョン原因っぽい
    https://zenn.dev/pontagon333/articles/425296e73487e2
  - なぜかNodeのバージョンが12になってた(謎)
    切り替え
    `nvs use 20.10.0`

* リトライ --> OK!
* コンパイル
  - `cd sample`
  - `npm run dev`
  - http://localhost:3000へアクセス
    - 確認OK (アクセス時にコンパイルしてる??そういう仕組みなのか)
