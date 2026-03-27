# レッスン 2: 基本コマンド

## 🎯 目標

Gitの日常的なワークフロー（変更の記録・共有）を習得します。

---

## Gitの基本的な流れ

```
作業ディレクトリ  →(git add)→  ステージング  →(git commit)→  ローカルリポジトリ
                                                                       ↓
                                                               (git push)
                                                                       ↓
                                                               リモートリポジトリ (GitHub)
```

---

## 1. リポジトリの作成・クローン

### 新しいリポジトリを作成する

```bash
mkdir my-project
cd my-project
git init
```

### GitHubからクローンする

```bash
git clone git@github.com:<ユーザー名>/<リポジトリ名>.git
cd <リポジトリ名>
```

---

## 2. 変更をステージングする (`git add`)

```bash
# 特定のファイルをステージング
git add ファイル名

# 変更されたすべてのファイルをステージング
git add .

# ステージングの状態を確認
git status
```

---

## 3. コミットする (`git commit`)

ステージングした変更をリポジトリに記録します。

```bash
git commit -m "コミットメッセージ"
```

良いコミットメッセージの例：

- ✅ `Add login feature`
- ✅ `Fix bug in score calculation`
- ❌ `修正` （何を修正したか不明）
- ❌ `aaa` （意味がない）

---

## 4. 変更をプッシュする (`git push`)

ローカルの変更をGitHubに送ります。

```bash
git push origin main
```

---

## 5. 変更を取得する (`git pull`)

GitHubの変更をローカルに取り込みます。

```bash
git pull origin main
```

---

## 6. 履歴を確認する (`git log`)

```bash
# 基本的なログ
git log

# 1行で表示
git log --oneline

# グラフ付きで表示
git log --oneline --graph --all
```

---

## 7. 差分を確認する (`git diff`)

```bash
# 作業ディレクトリとステージングの差分
git diff

# ステージングとリポジトリの差分
git diff --staged
```

---

## 📝 よく使うコマンド一覧

| コマンド | 説明 |
|---------|------|
| `git init` | リポジトリを初期化 |
| `git clone <URL>` | リモートからクローン |
| `git status` | 状態を確認 |
| `git add <ファイル>` | ステージングに追加 |
| `git commit -m "メッセージ"` | コミット |
| `git push origin <ブランチ>` | リモートにプッシュ |
| `git pull origin <ブランチ>` | リモートから取得 |
| `git log --oneline` | コミット履歴を確認 |
| `git diff` | 差分を確認 |

---

## 🏋️ 演習

このリポジトリを使って練習してみましょう！

1. `introduce_yourself/` ディレクトリに自己紹介ファイルを作成する
2. `git add` でステージング
3. `git commit -m "Add introduction: <自分の名前>"` でコミット
4. `git push` でGitHubに送る

---

## ✅ チェックリスト

- [ ] `git init` または `git clone` でリポジトリを用意できる
- [ ] `git add` と `git commit` で変更を記録できる
- [ ] `git push` でGitHubに変更を送れる
- [ ] `git pull` でGitHubの変更を取り込める
- [ ] `git log --oneline` でコミット履歴を確認できる

---

## ➡️ 次のレッスン

[レッスン 3: ブランチ入門](../03_branching_basics/README.md)
