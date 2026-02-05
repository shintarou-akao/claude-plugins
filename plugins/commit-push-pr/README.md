# commit-push-pr

コミット・プッシュ・PR作成までの一連の手順を自動実行するプラグイン。

## 含まれるスキル

| スキル名 | コマンド | 説明 |
|---------|---------|------|
| commit-push-pr | `/commit-push-pr` | `commit` → `push` → `pr-generator` を順番に実行 |

## 依存プラグイン

以下の3つが導入されていること:

- `commit`
- `push`
- `pr-generator`

## 使い方

1. `git add` でコミットする変更をステージする
2. `/commit-push-pr` を実行
3. コミット → プッシュ → PR作成まで自動で進行される
