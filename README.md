# claude-plugins

Claude Code プラグイン配布用マーケットプレースリポジトリ。

## リポジトリ構成

```
claude-plugins/
├── .claude-plugin/
│   └── marketplace.json          # マーケットプレース定義
├── plugins/
│   └── {plugin-name}/            # プラグインディレクトリ
│       ├── .claude-plugin/
│       │   └── plugin.json       # プラグインメタデータ
│       ├── skills/
│       │   └── {skill-name}/
│       │       └── SKILL.md      # スキル定義
│       └── README.md
├── .gitignore
├── LICENSE
└── README.md
```

## インストール方法

```bash
# マーケットプレース追加
/plugin marketplace add shintaro/claude-plugins

# プラグインインストール
/plugin install my-first-skill@shintaro-plugins
```

## 新しいプラグインを追加する

1. `plugins/` 以下に新しいディレクトリを作成
2. `.claude-plugin/plugin.json` とスキル定義を配置
3. `.claude-plugin/marketplace.json` の `plugins` 配列に追記
4. コミットしてプッシュ

## ライセンス

MIT License - [LICENSE](./LICENSE)
