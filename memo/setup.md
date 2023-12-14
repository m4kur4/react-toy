## 手順 (macOS)
nvsをインストール
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