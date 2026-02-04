---
name: push
description: 現在のブランチをリモートにプッシュする。
---

# プッシュ

現在のブランチをリモートリポジトリにプッシュする。

## ワークフロー

1. `git rev-parse --abbrev-ref HEAD` で現在のブランチ名を取得
2. `git push -u origin <ブランチ名>` でプッシュ実行
