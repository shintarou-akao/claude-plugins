# my-first-skill

サンプルプラグイン。Claude Code スキルの基本構成を示す例です。

## 含まれるスキル

| スキル名 | コマンド | 説明 |
|---------|---------|------|
| example-skill | `/example-skill` | 基本的なスキル動作のデモ |

## 開発・カスタマイズ

新しいスキルを追加する場合:

1. `skills/` 以下に新しいディレクトリを作成
2. `SKILL.md` を配置（YAML frontmatter が必須）
3. `../.claude-plugin/plugin.json` の `skills` 配列に追記
