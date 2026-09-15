# Quickstart — ChatGPTで使う

Reddit RadarはCodex専用ではない。

普段のChatGPTチャットから使う。

## 最短コマンド

### 宣伝機会を探す

```text
Reddit Radar、<プロジェクト名>で。
最近のRedditから参加価値の高いスレを探して、上位5件。
```

### 市場調査

```text
Reddit Radarで「<テーマ>」の需要調査。
最近の投稿を中心に、繰り返し出る悩み・既存手段への不満・反対意見までまとめて。
```

### 1スレ分析

```text
Reddit Radarでこのスレ分析して。
宣伝してよいか、Promotion Riskと返信案まで。
<URL>
```

### 返信だけ

```text
このReddit投稿に返信したい。
Reddit Radarのルールで、宣伝なし版とsoft mention版を作って。
<URL>
```

## GitHubを正本として使う

このrepositoryの内容は更新される可能性があるため、可能なら調査開始時に最新版の以下を参照する。

1. `SKILL.md`
2. `docs/SCORING.md`
3. `docs/SAFETY.md`
4. 必要に応じて対象project file

古いチャット上の記憶より、GitHubの現行ファイルを優先する。

## プロジェクト情報が足りない場合

毎回細かく質問する必要はない。

最低限わかっている範囲で検索を開始し、結果に影響する重大な不足だけ明示する。

特に次があると精度が上がる。

- 何を広めたいか
- どんな人に届けたいか
- 相手に提供できる価値
- 絶対に避けたい宣伝方法
- 公式URL（必要な場合のみ）

## APIについて

このPhase 1ではユーザー自身のOpenAI APIキーを使わない。

ChatGPT内の通常のWeb調査と文章生成として実行する。

GitHubも「APIを動かす場所」ではなく、ルールとプロジェクト情報を置く場所として使う。

## 定期監視したい場合

例:

```text
毎朝、Reddit Radarでweb fiction / indie author周辺を確認して、
Opportunity Score 85以上の新規候補があるときだけ教えて。
```

定期チェックを使う場合も、最終的なReddit投稿は人間が行う。
