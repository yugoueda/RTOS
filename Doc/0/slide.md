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
# Zephyr SDKのダウンロード
git clone https://github.com/zephyrproject-rtos/zephyr.git

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

