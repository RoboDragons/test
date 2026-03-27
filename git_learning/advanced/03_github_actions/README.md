# レッスン 3: GitHub Actions

## 🎯 目標

GitHub Actionsを使って、テスト・ビルド・デプロイを自動化できるようになります。

---

## GitHub Actions とは？

コードのプッシュやPRをトリガーに、自動でジョブを実行する CI/CD ツールです。

```
開発者がpush/PRを作成
         ↓
GitHub Actionsが起動
         ↓
 ┌──────────────────┐
 │  ビルド           │
 │  テスト           │
 │  コードチェック    │
 └──────────────────┘
         ↓
成功 → マージ可能・自動デプロイ
失敗 → 開発者に通知
```

---

## 1. ワークフローファイルの構造

ワークフローは `.github/workflows/` ディレクトリに YAML で書きます。

```yaml
# .github/workflows/ci.yml

name: CI  # ワークフロー名

on:              # トリガー
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:            # ジョブ定義
  build:
    runs-on: ubuntu-latest  # 実行環境

    steps:
      - uses: actions/checkout@v4   # コードをチェックアウト
      
      - name: Install dependencies
        run: |
          sudo apt-get update
          sudo apt-get install -y cmake
      
      - name: Build
        run: |
          cmake -B build
          cmake --build build
      
      - name: Run tests
        run: |
          cd build && ctest --verbose
```

---

## 2. よく使うトリガー

```yaml
on:
  push:                    # プッシュ時
    branches: [ main ]
  pull_request:            # PR作成・更新時
    branches: [ main ]
  schedule:                # 定期実行
    - cron: '0 9 * * 1'   # 毎週月曜9時
  workflow_dispatch:        # 手動実行
```

---

## 3. よく使うアクション

```yaml
steps:
  # コードをチェックアウト
  - uses: actions/checkout@v4

  # キャッシュを活用（ビルド高速化）
  - uses: actions/cache@v3
    with:
      path: ~/.cache
      key: ${{ runner.os }}-cache-${{ hashFiles('**/CMakeLists.txt') }}

  # PRにコメントを投稿
  - uses: actions/github-script@v7
    with:
      script: |
        github.rest.issues.createComment({
          issue_number: context.issue.number,
          owner: context.repo.owner,
          repo: context.repo.repo,
          body: 'ビルド成功！'
        })
```

---

## 4. シークレット（機密情報）の管理

APIキーやパスワードはコードに書かず、GitHubのシークレット機能を使います。

**設定場所：** Settings → Secrets and variables → Actions → New repository secret

```yaml
steps:
  - name: Deploy
    env:
      API_KEY: ${{ secrets.MY_API_KEY }}
    run: ./deploy.sh
```

---

## 5. C++プロジェクト向けの例

```yaml
name: C++ CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Install dependencies
        run: sudo apt-get install -y cmake g++
      
      - name: Configure CMake
        run: cmake -B build -DCMAKE_BUILD_TYPE=Release
      
      - name: Build
        run: cmake --build build
      
      - name: Test
        run: cd build && ctest
```

---

## ✅ チェックリスト

- [ ] `.github/workflows/` にワークフローファイルを作成できる
- [ ] push/PR時に自動でビルド・テストが走るCIを設定できる
- [ ] GitHub Actionsのログを見てエラーを調査できる
- [ ] シークレットを使って機密情報を安全に扱える

---

## 🎉 学習プログラム修了！

上級まで修了しました！おめでとうございます！  
学んだことを活かして、チームの開発をリードしていきましょう。

- [演習一覧に戻る](../../exercises/README.md)
- [学習プログラムトップに戻る](../../README.md)
