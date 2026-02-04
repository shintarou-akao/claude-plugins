---
name: interview
argument-hint: [instructions]
description: ユーザーに詳細なインタビューを行い、仕様書を生成する。
allowed-tools: AskUserQuestion, Write
---

# インタビュー

`[instructions]` を出発点とし、AskUserQuestion を使って段階的にインタビューを行う。
全体像・目的から技術的制約・機能詳細へと複数ラウンドかけて深掘りする。
明白な質問は避け、実装に直結する質問を優先する。

ユーザーが終了の意思を示した時点、あるいは主要項目がカバーされた時点で、
仕様書として書き出す。書き出し前にファイル名や出力先を確認する。
