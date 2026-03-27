# レッスン 2: リモート操作

## 🎯 目標

リモートリポジトリとのやり取りを深く理解し、`fetch` / `pull` / `push` を使い分けます。

---

## 1. リモートの確認

```bash
# リモートの一覧
git remote -v

# 例:
# origin  git@github.com:RoboDragons/test.git (fetch)
# origin  git@github.com:RoboDragons/test.git (push)
```

---

## 2. `git fetch` vs `git pull`

| コマンド | 動作 |
|---------|------|
| `git fetch` | リモートの変更を取得するが、ローカルブランチには自動でマージしない |
| `git pull` | `git fetch` + `git merge` を一度に行う |

### fetch を使う場面

変更内容を確認してからマージしたい場合：

```bash
git fetch origin
git log origin/main --oneline  # リモートの変更を確認
git merge origin/main          # 問題なければマージ
```

### pull を使う場面

すぐに取り込んで問題ない場合：

```bash
git pull origin main
```

---

## 3. プッシュ

```bash
# ブランチをリモートにプッシュ
git push origin feature/my-feature

# 初回プッシュ（上流ブランチを設定）
git push -u origin feature/my-feature

# 上流ブランチ設定後は省略可能
git push
```

---

## 4. リモートブランチの追跡

```bash
# リモートブランチを元にローカルブランチを作成
git checkout -b feature/remote-branch origin/feature/remote-branch

# または
git switch --track origin/feature/remote-branch
```

---

## 5. 強制プッシュ（注意が必要！）

```bash
# ローカルの状態でリモートを上書き（チームでは慎重に！）
git push --force-with-lease origin feature/my-feature
```

> ⚠️ `--force` より安全な `--force-with-lease` を使いましょう。  
> 他の人の変更を上書きしてしまう危険があります。

---

## 6. リモートブランチの削除

```bash
git push origin --delete feature/old-branch
```

---

## ✅ チェックリスト

- [ ] `git fetch` と `git pull` の違いを説明できる
- [ ] `git push -u origin <ブランチ>` で上流ブランチを設定できる
- [ ] リモートブランチを元にローカルブランチを作成できる
- [ ] `git push --force-with-lease` の危険性を理解している

---

## ➡️ 次のレッスン

[レッスン 3: GitHubの機能活用](../03_github_features/README.md)
