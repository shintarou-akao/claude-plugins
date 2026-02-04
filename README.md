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

# プラグインインストール（例）
/plugin install commit@shintaro-plugins
/plugin install implement@shintaro-plugins
/plugin install interview@shintaro-plugins
/plugin install pr-generator@shintaro-plugins
/plugin install pr-review-respond@shintaro-plugins
/plugin install push@shintaro-plugins
/plugin install skill-update@shintaro-plugins
/plugin install spec-plan@shintaro-plugins
```

## 新しいプラグインを追加する

1. `plugins/` 以下に新しいディレクトリを作成
2. `.claude-plugin/plugin.json` とスキル定義を配置
3. `.claude-plugin/marketplace.json` の `plugins` 配列に追記
4. コミットしてプッシュ

## ライセンス

MIT License - [LICENSE](./LICENSE)
