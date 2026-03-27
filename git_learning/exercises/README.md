# 🏋️ 演習一覧

学んだ内容を実際に手を動かして定着させましょう。

---

## 🟢 初級演習

### 演習 1: 自己紹介ファイルを追加する

**目標:** 基本的なGit操作（add/commit/push）の練習

**手順:**

1. このリポジトリをクローンする（まだの場合）
   ```bash
   git clone git@github.com:RoboDragons/test.git
   cd test
   ```

2. `introduce_yourself/<学年>/` ディレクトリに自分の名前のファイルを作成する
   ```bash
   # 例: 1年生の場合
   echo "名前: 山田太郎\n趣味: ロボット制作" > introduce_yourself/first_grade/yamada_taro
   ```

3. ステージング・コミット・プッシュ
   ```bash
   git add introduce_yourself/first_grade/yamada_taro
   git commit -m "Add introduction: yamada_taro"
   git push origin main
   ```

---

### 演習 2: ブランチを使って自己紹介を更新する

**目標:** ブランチの作成・コミット・プッシュの練習

**手順:**

1. 作業ブランチを作成する
   ```bash
   git checkout -b feature/update-intro-<自分の名前>
   ```

2. 自己紹介ファイルを更新する

3. コミットしてプッシュ
   ```bash
   git add .
   git commit -m "Update introduction: <自分の名前>"
   git push origin feature/update-intro-<自分の名前>
   ```

4. GitHubでPull Requestを作成する

---

## 🟡 中級演習

### 演習 3: コンフリクトを体験する

**目標:** コンフリクトの発生と解消を体験する

**手順:**

1. `main` から `branch-a` と `branch-b` を作成する
   ```bash
   git checkout -b branch-a main
   ```

2. `branch-a` で `conflict_practice.txt` を作成してコミット
   ```
   # conflict_practice.txt
   branch-a の変更内容
   ```

3. `main` に戻り `branch-b` を作成
   ```bash
   git checkout main
   git checkout -b branch-b
   ```

4. `branch-b` でも同じファイルを作成してコミット
   ```
   # conflict_practice.txt
   branch-b の変更内容
   ```

5. `main` に `branch-a` をマージし、続いて `branch-b` をマージしてコンフリクトを解消する
   ```bash
   git checkout main
   git merge branch-a
   git merge branch-b  # ← コンフリクト発生！
   # ファイルを編集してコンフリクトを解消
   git add conflict_practice.txt
   git commit -m "Resolve merge conflict"
   ```

---

### 演習 4: Pull Request を出してレビューを受ける

**目標:** チーム開発のワークフローを体験する

**手順:**

1. Issueを作成する（例: 「README を更新する」）
2. ブランチを作成して変更を加える
3. PRを作成し、Issueとリンクさせる（`Close #<Issue番号>`）
4. チームメンバーにレビューを依頼する
5. フィードバックを受けて修正する
6. 承認後にマージする

---

## 🔴 上級演習

### 演習 5: インタラクティブリベースでコミットを整理する

**目標:** `git rebase -i` を使いこなす

**手順:**

1. 作業ブランチで複数の細かいコミットを作成する
   ```bash
   git checkout -b feature/rebase-practice
   echo "1" > file.txt && git add . && git commit -m "WIP: step 1"
   echo "2" >> file.txt && git add . && git commit -m "WIP: step 2"
   echo "3" >> file.txt && git add . && git commit -m "WIP: step 3"
   ```

2. インタラクティブリベースで3つのコミットを1つにまとめる
   ```bash
   git rebase -i HEAD~3
   # 2つ目と3つ目を "squash" に変更する
   ```

3. まとめた後のコミットメッセージを整える

---

### 演習 6: GitHub Actionsでシンプルなワークフローを作る

**目標:** CI/CDの基礎を理解する

**手順:**

1. `.github/workflows/hello.yml` を作成する
   ```yaml
   name: Hello World
   on: [push]
   jobs:
     hello:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v4
         - name: Say hello
           run: echo "Hello, RoboDragons!"
   ```

2. コミット・プッシュして Actions タブでワークフローが実行されることを確認する

---

## 📊 進捗管理

| 演習 | レベル | 完了 |
|------|--------|------|
| 演習1: 自己紹介ファイルを追加 | 🟢 初級 | |
| 演習2: ブランチを使って更新 | 🟢 初級 | |
| 演習3: コンフリクトを体験 | 🟡 中級 | |
| 演習4: PR・レビューを体験 | 🟡 中級 | |
| 演習5: インタラクティブリベース | 🔴 上級 | |
| 演習6: GitHub Actions設定 | 🔴 上級 | |
