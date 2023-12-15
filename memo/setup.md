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