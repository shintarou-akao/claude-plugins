# pr-generator

PRテンプレートと変更差分を元に下書きを自動生成し、draft PRを作成するプラグイン。

## 含まれるスキル

| スキル名 | コマンド | 説明 |
|---------|---------|------|
| pr-generator | `/pr-generator` | PR下書き自動生成・draft PR作成 |

## 使い方

1. `/pr-generator` を実行
2. ベースブランチとコミット範囲を選択
3. テンプレートがある場合は自動検出・適用
4. 下書きを確認・承認
5. `gh pr create --draft` で PR が作成される

## テンプレート検索順

複数テンプレートがある場合は選択画面が表示される。

1. `.github/PULL_REQUEST_TEMPLATE/*.md`
2. `docs/PULL_REQUEST_TEMPLATE/*.md`
3. `PULL_REQUEST_TEMPLATE/*.md`
4. `.github/pull_request_template.md`
5. `docs/pull_request_template.md`
6. `pull_request_template.md`
