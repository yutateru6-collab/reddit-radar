# Existing Open-Source Projects

調査日: 2026-09-16

Reddit Radarを考える際に参考にした既存OSS。現段階ではForkして本番利用するのではなく、設計思想を参考にする。

## 1. RedSignal

Repository: https://github.com/ivucicev/redsignal

### 参考になる点

- Redditをキーワード・subredditで監視
- AIフィルタで関連度を絞る
- 投稿・コメントをフィード化
- スレッド文脈を確認
- AIによる返信草案
- Lead状態管理
- Analytics
- Slack / Telegram通知
- SQLite
- Docker
- MIT License

### Reddit Radarとの関係

最も近い発想。

特に以下を参考にする。

- 「見つける → 絞る → 返信を考える」の流れ
- 投稿を単なる検索結果ではなく、行動候補として管理する発想
- AIを検索の代替ではなくノイズ除去に使う考え方

### 今すぐForkしない理由

RedSignalは独立サーバーとして運用する前提で、Reddit API認証やAI provider設定が必要になる。

現在のReddit RadarはChatGPT内で直接使い、追加のAPIキー管理を増やさない方針なので、機能を丸ごと採用しない。

---

## 2. Harken

Repository: https://github.com/VladUZH/harken

### 参考になる点

- Self-hosted social listening
- Reddit以外にHacker News / Bluesky / Stack Overflow / RSS / X / YouTube等を扱う設計
- キーワード追跡
- sentiment
- theme clustering
- project grouping
- alerts
- dashboard / CLI
- SQLite
- LLMを必須にしない設計
- MIT License

### Reddit Radarとの関係

「宣伝先探し」から「市場調査」へ広げる際に非常に参考になる。

特に、個別投稿だけでなく複数投稿を横断してテーマを抽出する思想を取り入れる。

### 将来候補

Reddit Radarを将来 `Internet Radar` に広げる場合、Harken型のsource adapter設計を検討する。

---

## 3. RedoraAI

Repository: https://github.com/donebyai-team/RedoraAI

### 参考になる点

- Reddit lead discovery
- keyword / subreddit suggestion
- LLM scoring
- comment / DM generation
- monitoring
- scheduling
- reporting
- Reddit OAuth
- Next.js / Go / PostgreSQL / Redis
- MIT License

### Reddit Radarとの関係

Opportunity Scoreや「関連会話をAIで見つける」思想が近い。

### 採用しない部分

- 自動DM
- scheduled auto-replies
- multiple account rotation
- ban回避を意識したアカウント運用

Reddit Radarでは、人間確認を外さない。

---

## 4. Reddit Devvit

Official repository / templates:

- https://github.com/reddit/devvit
- https://github.com/reddit/devvit-template-react
- https://github.com/reddit/devvit-mcp

### 参考になる点

将来、Reddit内部アプリとして実装する場合の公式基盤。

Devvit WebではReddit APIへサーバー側からアクセスでき、検索等の機能も公式SDK側で提供されている。

### 現在の判断

Phase 1では使わない。

理由:

- ChatGPTのWeb検索で目的を満たせる
- 独立アプリの保守を増やさない
- APIキーやサーバーを増やさない
- まず実際の運用でOpportunity Scoreが有効か検証したい

実地検証で価値が確認できた後のみ、Devvit版を検討する。

---

# 結論

現在の最適構成は次。

```text
GitHub
  = ルール・採点基準・ワークフローの正本

ChatGPT
  = Reddit検索・読解・分析・返信作成

User
  = 最終判断・実際の投稿
```

ゼロから大規模アプリを作る前に、この最小構成で価値を検証する。
