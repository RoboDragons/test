# レッスン 1: ブランチのマージ

## 🎯 目標

ブランチをマージする方法と、コンフリクトの解消方法を習得します。

---

## 1. マージ (`git merge`)

別ブランチの変更を現在のブランチに取り込みます。

```bash
# main ブランチに feature ブランチをマージする
git checkout main
git merge feature/my-feature
```

### Fast-forward マージ

```
マージ前:
main:    A --- B
                \
feature:         C --- D

マージ後 (fast-forward):
main:    A --- B --- C --- D
```

### 3-way マージ

```
マージ前:
main:    A --- B --- E
                \
feature:         C --- D

マージ後 (merge commit):
main:    A --- B --- E --- M
                \         /
feature:         C --- D
```

---

## 2. コンフリクト（競合）の解消

同じファイルの同じ行を別々のブランチで変更すると「コンフリクト」が発生します。

```bash
git merge feature/my-feature
# CONFLICT (content): Merge conflict in file.txt
# Automatic merge failed; fix conflicts and then commit the result.
```

コンフリクトが起きたファイルの中身：

```
<<<<<<< HEAD
mainブランチの内容
=======
featureブランチの内容
>>>>>>> feature/my-feature
```

**解消手順：**

1. コンフリクトしたファイルを編集し、残したい内容に書き換える
2. `<<<<<<<`, `=======`, `>>>>>>>` の行を削除する
3. `git add <ファイル名>` でステージング
4. `git commit` でマージコミットを作成

```bash
# コンフリクトの確認
git status

# 解消後
git add conflicted-file.txt
git commit -m "Merge feature/my-feature into main"
```

---

## 3. マージを中止する

```bash
git merge --abort
```

---

## 🏋️ 演習

1. `main` から `feature/merge-practice` ブランチを作成する
2. 同じファイルを `main` と `feature/merge-practice` の両方で変更する
3. `main` に `feature/merge-practice` をマージしてコンフリクトを解消する

---

## ✅ チェックリスト

- [ ] `git merge` でブランチをマージできる
- [ ] コンフリクトの発生原因を説明できる
- [ ] コンフリクトを手動で解消してコミットできる
- [ ] `git merge --abort` でマージを中止できる

---

## ➡️ 次のレッスン

[レッスン 2: リモート操作](../02_remote_operations/README.md)
