---
name: commit
description: ステージされた変更から日本語のConventional Commitメッセージを生成し、コミットを実行する。
---

# コミット

ステージされた変更内容を分析し、日本語のConventional Commit形式で最適なコミットメッセージを生成してコミットを実行する。

## ワークフロー

### 1. ステージされた変更の確認

以下のコマンドを実行:

- `git diff --cached --stat` - 変更ファイル一覧
- `git diff --cached` - 詳細な差分

変更がない場合は通知して終了。

### 2. コミットメッセージの生成

変更内容を分析し、**Conventional Commit形式**で最適な日本語コミットメッセージを**1つ**生成。

**フォーマット**: `type(scope): 説明`（日本語、50文字以内推奨）

### 3. コミットの実行

生成したメッセージの末尾に `Co-Authored-By`署名を付けて実行。HEREDOCを使って署名の改行を正確に保つこと。

```bash
git commit -m "$(cat <<'EOF'
<生成したコミットメッセージ>

Co-Authored-By: Claude <noreply@anthropic.com>
EOF
)"
```
