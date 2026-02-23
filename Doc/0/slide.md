---
marp: true
theme: default
paginate: true
footer: RTOS勉強会 第0回
---

# RTOS勉強会 第0回
## 環境構築

---

## 今回の目標

- RTOS開発環境をセットアップする
- 動作確認を行う
- 次回以降の実習に向けて準備をする

---

## 環境構築の流れ
### 参考サイト
https://tech-and-investment.com/raspberrypi-pico2-05-zephyr01/

1. 必要なツールのインストール
2. Zephyr RTOS のセットアップ
3. サンプルプロジェクトのビルド
4. 動作確認

---

## ステップ 1: 必要なツール

### インストール対象
- **Python 3.8 以上**
- **Git**
- **CMake 3.20 以上**
- **Ninja**（ビルドツール）
- **ボードサポート**（QEMU または実機）

---


## ステップ 2: Zephyr RTOS セットアップ

```bash
# 管理者権限のpowershellで実行する
# chocolateyのインストール
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

# 確認メッセージの無効化
choco feature enable -n allowGlobalConfirmation

# cmakeインストール
choco install cmake --installargs 'ADD_CMAKE_TO_PATH=System'

#その他関連ツールのインストール
choco install ninja gperf python311 git dtc-msys2 wget 7zip
```

---

## ステップ 2: Python仮想環境の整備

```bash
# 通常ユーザのpowershellで実行する
# 仮想環境の作成
python -m venv zephyrproject\.venv
# 仮想環境のアクティブ化
zephyrproject\.venv\Scripts\activate.bat

#batの実行に以下が必要かも
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned

```
---

## ステップ 2: Python仮想環境の整備

```bash
# 通常ユーザのpowershellで実行する
# westインストール
pip install west

# west初期化
west init ~/zephyrproject

# 作成したディレクトリに移動
cd ~/zephyrproject

#更新
west update

west zephyr-export

west packages pip --install
```

---

## ステップ 2: Zephyr RTOS セットアップ

```bash
# Zephyr SDKのダウンロード
cd %HOMEPATH%\zephyrproject\zephyr
west sdk install

# 依存パッケージのインストール
pip install -r zephyr/requirements.txt

# 環境変数の設定
export ZEPHYR_BASE=~/zephyr
```

---

## ステップ 3: サンプルプロジェクトのビルド

```bash
# Hello World アプリケーション
cd zephyr/samples/hello_world

# ビルド
west build -b native_sim

# 実行
./build/zephyr/zephyr.elf
```

---

## ステップ 4: 動作確認

✅ サンプルが正常にビルドできたか
✅ 実行結果が表示されたか
✅ エラーはないか

これで環境構築は完了です！

---

## 次回の予告

### 第1回：RTOSとは何かを体験で掴む

- RTOSとLinuxの違い
- リアルタイム性を体験する
- ジッタを観察する

---

## 質問・トラブルシューティング

**よくある問題：**
- Python バージョンが古い → 3.8 以上に更新
- CMake が見つからない → PATH を確認
- west コマンドが見つからない → `pip install west`

---

## 終了

質問があればお気軽にどうぞ！

