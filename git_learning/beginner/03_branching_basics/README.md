# レッスン 3: ブランチ入門

## 🎯 目標

ブランチの概念を理解し、ブランチの作成・切り替えができるようになります。

---

## ブランチとは？

ブランチは「作業の分岐点」です。  
`main` ブランチを汚さずに、機能開発やバグ修正を独立した環境で行えます。

```
main:     A --- B --- C
                       \
feature:               D --- E
```

---

## 1. ブランチの確認

```bash
# ローカルブランチの一覧
git branch

# すべてのブランチ（リモート含む）
git branch -a
```

---

## 2. ブランチの作成

```bash
# ブランチを作成
git branch feature/my-feature

# ブランチを作成して同時に切り替える（推奨）
git checkout -b feature/my-feature

# 新しい書き方 (Git 2.23+)
git switch -c feature/my-feature
```

---

## 3. ブランチの切り替え

```bash
# ブランチを切り替える
git checkout main

# 新しい書き方 (Git 2.23+)
git switch main
```

---

## 4. ブランチの命名規則

チームで作業する場合、わかりやすい名前をつけましょう：

| プレフィックス | 用途 | 例 |
|---|---|---|
| `feature/` | 新機能の追加 | `feature/add-login` |
| `fix/` | バグ修正 | `fix/score-bug` |
| `docs/` | ドキュメント更新 | `docs/update-readme` |
| `refactor/` | リファクタリング | `refactor/cleanup-main` |

---

## 5. ブランチの削除

```bash
# マージ済みブランチを削除
git branch -d feature/my-feature

# 強制削除
git branch -D feature/my-feature
```

---

## 🏋️ 演習

1. `feature/introduce-<自分の名前>` という名前でブランチを作成する
2. そのブランチに切り替える
3. `introduce_yourself/` に自己紹介ファイルを追加する
4. コミットしてプッシュする

```bash
git checkout -b feature/introduce-yourname
# ファイルを作成・編集
git add .
git commit -m "Add introduction: yourname"
git push origin feature/introduce-yourname
```

---

## ✅ チェックリスト

- [ ] `git branch` でブランチ一覧を確認できる
- [ ] `git checkout -b <ブランチ名>` で新しいブランチを作れる
- [ ] `git checkout <ブランチ名>` でブランチを切り替えられる
- [ ] ブランチごとに独立した変更ができることを理解した

---

## ➡️ 次のステップ

初級を修了しました！🎉  
[中級へ進む](../../intermediate/README.md)
