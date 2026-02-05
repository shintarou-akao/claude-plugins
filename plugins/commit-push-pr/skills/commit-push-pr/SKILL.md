---
name: commit-push-pr
description: コミット・プッシュ・PR作成までの一連の手順を自動実行するオーケストレータスキル。内部的に `commit` → `push` → `pr-generator` の3スキルを順番に実行する。依存スキルとして `commit`・`push`・`pr-generator` が導入されていること。
---

# commit-push-pr

`commit` → `push` → `pr-generator` を順番に呼び出し、コミットからPR作成までを一連で実行する。

## 依存スキル

以下の3つが導入・有効であること:

- `commit`
- `push`
- `pr-generator`

いずれかが利用不可の場合は、その旨を通知して停止する。

## ワークフロー

各ステップで Skill ツールを使用し、完了を確認してから次へ進む。途中で失敗した場合は停止し、失敗箇所と理由を通知する。

1. Skill ツールで `commit` を実行
2. `commit` が正常完了したら、Skill ツールで `push` を実行
3. `push` が正常完了したら、Skill ツールで `pr-generator` を実行
