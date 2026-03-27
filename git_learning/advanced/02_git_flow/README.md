# レッスン 2: Gitフロー

## 🎯 目標

チームでの開発に適したブランチ戦略を理解し、運用できるようになります。

---

## 代表的なブランチ戦略

### 1. GitHub Flow（シンプル・推奨）

```
main (常にデプロイ可能)
  ├── feature/add-login
  ├── fix/score-bug
  └── docs/update-readme
```

**ルール：**
- `main` は常にリリース可能な状態を保つ
- 作業は必ずブランチを切って行う
- PRを通じてのみ `main` にマージする

**流れ：**

```bash
# 1. mainから作業ブランチを作成
git checkout -b feature/new-feature main

# 2. 開発・コミット
git add .
git commit -m "Add new feature"

# 3. プッシュしてPRを作成
git push origin feature/new-feature
# → GitHub でPR作成 → レビュー → マージ

# 4. マージ後はブランチを削除
git branch -d feature/new-feature
git push origin --delete feature/new-feature
```

---

### 2. Git Flow（大規模・リリース管理あり）

```
main      (リリース用)
develop   (開発用)
  ├── feature/add-login     (機能開発)
  ├── release/v1.0.0        (リリース準備)
  └── hotfix/critical-bug   (緊急バグ修正)
```

| ブランチ | 役割 |
|---------|------|
| `main` | 本番環境 (リリース済みのみ) |
| `develop` | 開発の統合ブランチ |
| `feature/*` | 機能開発 |
| `release/*` | リリース準備・テスト |
| `hotfix/*` | 本番の緊急修正 |

---

## RoboDragonsでの推奨フロー

シンプルな **GitHub Flow** ベースで運用しましょう。

```bash
# 1. mainの最新を取得
git checkout main
git pull origin main

# 2. 作業ブランチを作成
git checkout -b feature/<機能名>

# 3. 開発
# ... コードを書く ...
git add .
git commit -m "わかりやすいメッセージ"

# 4. プッシュ
git push origin feature/<機能名>

# 5. GitHub でPRを作成してレビューを依頼

# 6. レビュー承認後にマージ
# (GitHubのUIからマージ)

# 7. ローカルのブランチを削除
git checkout main
git pull origin main
git branch -d feature/<機能名>
```

---

## ブランチ保護ルール（Branch Protection）

GitHubのリポジトリ設定で `main` ブランチを保護できます：

- **Require pull request reviews** → PRのレビューが必須
- **Require status checks to pass** → CIが通らないとマージ不可
- **Restrict who can push** → 直接プッシュを制限

**設定場所：** Settings → Branches → Add rule

---

## ✅ チェックリスト

- [ ] GitHub Flow の流れを説明できる
- [ ] feature ブランチを作成してPRでマージできる
- [ ] Git Flow の各ブランチの役割を説明できる
- [ ] ブランチ保護ルールを設定できる

---

## ➡️ 次のレッスン

[レッスン 3: GitHub Actions](../03_github_actions/README.md)
