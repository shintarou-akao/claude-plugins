---
name: pr-generator
description: PRテンプレートと変更差分を元にPR下書きを自動生成し、ghコマンドでdraft PRを作成する。
---

# PR作成

PRテンプレートと変更差分を元に下書きを生成し、確認後PRを作成する。

## ワークフロー

### 1. PRテンプレートの読み込み

以下の優先順位でテンプレートファイルを検索し、見つかった場合はその構造に従って下書きを生成すること。テンプレートが存在する場合、テンプレートの全セクションを埋めること。

**複数テンプレート（サブディレクトリ）を優先検索：**

1. `.github/PULL_REQUEST_TEMPLATE/*.md`
2. `docs/PULL_REQUEST_TEMPLATE/*.md`
3. `PULL_REQUEST_TEMPLATE/*.md`

複数テンプレートが見つかった場合はAskUserQuestionでユーザーに選択してもらう。

**単一テンプレートの検索順：**

1. `.github/pull_request_template.md`
2. `docs/pull_request_template.md`
3. `pull_request_template.md`

いずれのパスにも存在しない場合はテンプレートなしで進める。

> ファイル名は大文字小文字を区別しない。拡張子は `.md` か `.txt` のいずれかの場合がある。

### 2. ベースブランチの確認

AskUserQuestionツールを使用:

- header: "ベース"
- question: "マージ先のブランチを選択してください"
- options:
  - label: "main"
    description: "mainブランチ"
  - label: "develop"
    description: "developブランチ"
  - label: "その他"
    description: "別のブランチを指定"

### 3. コミット範囲の選択

AskUserQuestionツールを使用:

- header: "範囲"
- question: "PRに含めるコミット範囲を選択してください"
- options:
  - label: "ブランチ全体"
    description: "現在のブランチの全コミットを含める"
  - label: "最新コミット1件"
    description: "直近1件のコミットを対象"
  - label: "カスタム"
    description: "直近N件、コミットハッシュ、ブランチ名などを指定"

### 4. 差分の取得

選択に応じてgit diffを実行:

- **ブランチ全体**: `git diff <ベースブランチ>...HEAD` と `git log <ベースブランチ>..HEAD --oneline`
- **最新コミット1件**: `git diff HEAD~1..HEAD` と `git log -1 --oneline`
- **カスタム**: ユーザーに詳細を確認（例: 直近N件 → `HEAD~N..HEAD`、特定ハッシュ → `abc123..HEAD`）

### 5. 下書きの生成

テンプレートの各セクションに対応する内容を生成し、`~/.claude/pr-drafts/` に出力。

### 6. PR作成

ghコマンドでPRを作成。

```bash
gh pr create --draft --assignee @me --title "変更内容の要約" --body-file ~/.claude/pr-drafts/XXXX.md --base <選択したブランチ>
```

作成後、PRのURLを表示。
