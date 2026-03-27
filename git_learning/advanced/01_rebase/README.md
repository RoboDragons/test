# レッスン 1: リベース

## 🎯 目標

`git rebase` を使ってコミット履歴を整理できるようになります。

---

## rebase とは？

rebase はブランチの「付け替え」です。  
merge と異なり、マージコミットを作らずに履歴を一直線に保てます。

```
マージ前:
main:    A --- B --- E
                \
feature:         C --- D

git rebase の後:
main:    A --- B --- E
                      \
feature:               C' --- D'

git merge (fast-forward) の後:
main:    A --- B --- E --- C' --- D'
```

---

## 1. 基本的なリベース

```bash
# feature ブランチを main の最新に追従させる
git checkout feature/my-feature
git rebase main
```

---

## 2. インタラクティブリベース

過去のコミットをまとめたり、メッセージを編集できます。

```bash
# 直近3つのコミットを編集
git rebase -i HEAD~3
```

エディタが開き、以下のような画面が表示されます：

```
pick abc1234 Add login form
pick def5678 Fix typo in login form
pick ghi9012 Add login validation

# コマンド:
# p, pick   = コミットをそのまま使う
# r, reword = コミットメッセージを変更
# e, edit   = コミットの内容を変更
# s, squash = 前のコミットにまとめる
# f, fixup  = squashと同じだがメッセージは捨てる
# d, drop   = コミットを削除
```

例：2つのコミットを1つにまとめる（squash）

```
pick abc1234 Add login form
squash def5678 Fix typo in login form
pick ghi9012 Add login validation
```

---

## 3. cherry-pick

別のブランチの特定のコミットだけを取り込みます。

```bash
# コミットのSHAを確認
git log --oneline feature/other-branch

# 特定のコミットを取り込む
git cherry-pick <commit-sha>

# 複数のコミットを取り込む
git cherry-pick <sha1> <sha2>
```

---

## 4. merge vs rebase の使い分け

| | merge | rebase |
|---|---|---|
| 履歴 | マージコミットが残る（非線形） | 一直線になる（線形） |
| 安全性 | 安全 | プッシュ済みブランチでは危険 |
| 適した場面 | チームで共有するブランチ | 自分だけのfeatureブランチ整理 |

> ⚠️ **黄金律**: リモートにプッシュ済みのコミットは rebase しない！  
> 他の人の作業を壊す可能性があります。

---

## ✅ チェックリスト

- [ ] `git rebase <ブランチ>` でブランチを付け替えられる
- [ ] `git rebase -i` でコミットをまとめられる
- [ ] `git cherry-pick` で特定のコミットを取り込める
- [ ] merge と rebase の違いを説明できる

---

## ➡️ 次のレッスン

[レッスン 2: Gitフロー](../02_git_flow/README.md)
