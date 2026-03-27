# レッスン 1: Gitの環境構築

## 🎯 目標

Gitをインストールし、基本的な初期設定を行います。

---

## 1. Gitのインストール

### Windows

1. [Git for Windows](https://gitforwindows.org/) からインストーラをダウンロード
2. インストーラを実行し、デフォルト設定でインストール

### macOS

```bash
# Homebrew を使う場合
brew install git

# または Xcode Command Line Tools
xcode-select --install
```

### Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install git
```

---

## 2. インストールの確認

```bash
git --version
# 例: git version 2.39.0
```

---

## 3. 初期設定

Gitにあなたの名前とメールアドレスを登録します。  
コミットログに表示される情報です。

```bash
git config --global user.name "あなたの名前"
git config --global user.email "your.email@example.com"
```

設定を確認するには：

```bash
git config --list
```

---

## 4. SSHキーの設定（GitHubへの接続）

パスワードなしでGitHubと通信するためにSSHキーを設定します。

```bash
# SSHキーを生成
ssh-keygen -t ed25519 -C "your.email@example.com"

# 公開鍵を表示（GitHubに登録する）
cat ~/.ssh/id_ed25519.pub
```

表示された公開鍵を  
**GitHub → Settings → SSH and GPG keys → New SSH key**  
に貼り付けます。

接続テスト：

```bash
ssh -T git@github.com
# Hi <username>! You've successfully authenticated...
```

---

## ✅ チェックリスト

- [ ] `git --version` でバージョンが表示される
- [ ] `git config --list` に name と email が表示される
- [ ] `ssh -T git@github.com` で認証成功メッセージが表示される

---

## ➡️ 次のレッスン

[レッスン 2: 基本コマンド](../02_basic_commands/README.md)
