---
name: implement
description: planファイルに基づいて実装を実行し、チェックリストを更新しながら進捗を管理
argument-hint: "~/.claude/plan/XXX.md"
---

# Plan実行スキル

planファイルに基づいて実装を実行し、チェックリストを更新しながら進捗を管理します。

## 処理手順

### Step 1: planファイルの特定と読み込み

引数 `$ARGUMENTS` のplanファイルを読み込む。

AskUserQuestionで対象を確認：

- header: "対象PR"
- question: "実行するPRを選択してください"
- options:
  - label: "全PR"
    description: "全PRを順次実行"
  - label: "その他"
    description: "PR番号を指定"

### Step 2: PRセクションの解析

planファイルから対象のPRセクションを特定し、チェックリストの完了状況（`[x]` / `[ ]`）を確認。

### Step 3: PR内タスクの実行

**PR内のチェックリスト項目は確認なしで連続実行する：**

1. PR内の未完了チェックリスト項目を順次実行
2. 各項目完了時にplanファイルのチェックを更新（`[ ]` → `[x]`）
3. 全チェックリスト完了後、「検証」セクションの手順を実行
4. 検証完了後、検証項目もチェックを更新

PR内では個別のタスクごとに確認を求めない。タスクまたは検証が失敗した場合は自律的に修正を試み、対応する。

### Step 4: PR完了後の確認

**単一PR実行時**（PR番号を指定した場合）はAskUserQuestionで確認：

- header: "次のアクション"
- question: "次は何をしますか？"
- options:
  - label: "コミット/プッシュ/PR作成"
    description: "コミット・プッシュ・PR作成を続行する（推奨）"
  - label: "停止"
    description: "実装を一時停止（続きから再開可能）"

**複数PR実行時**（全PRを選択した場合）は確認なしで次のPRへ自動で進む。全PR完了後に上記の確認を行う。
