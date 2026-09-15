# Reddit Radar

Reddit上の「今、参加する価値がある会話」をChatGPTで見つけ、分析し、安全に返信案まで作るための運用リポジトリです。

## 目的

このリポジトリは、外部のOpenAI APIを使う独立Webアプリではありません。

普段のChatGPTで、たとえば次のように頼むためのルール・評価基準・出力形式を保存します。

- `Reddit Radar、ザリガニ英語版で`
- `Reddit Radar、VOCADONで`
- `Redditで英語学習アプリの不満を探して`
- `このRedditスレ、宣伝しても嫌われないか判定して`
- `この投稿に自然に返信する英語を3案作って`

ChatGPT側でWeb検索を行い、このリポジトリのルールに沿って候補を評価します。

## 重要方針

- **OpenAI APIキー不要**
- **追加のAPI課金を前提にしない**
- **Codex専用ではない**
- **普段のChatGPTチャットで使う**
- **自動投稿しない**
- **自動DMしない**
- **複数アカウントのローテーションをしない**
- **Redditの各subredditのルールを必ず確認する**
- **最終投稿は人間が確認してから行う**
- **宣伝より先に、会話への貢献を優先する**

## まず使う

最短手順は [`docs/QUICKSTART.md`](./docs/QUICKSTART.md) を参照。

たとえばChatGPTで次のように頼む。

```text
Reddit Radar、ザリガニ英語版で。
最近のRedditから参加価値の高いスレを探して、上位5件。
```

このrepoが参照できる場合は、古いチャット上の記憶より現行の `SKILL.md` / scoring / safety rules を優先する。

## Reddit Radarの基本フロー

```text
ユーザーが目的を伝える
        ↓
Reddit上の関連投稿・コメントを検索
        ↓
候補を絞る
        ↓
subredditルールと文脈を確認
        ↓
Opportunity Scoreを付ける
        ↓
日本語で要約
        ↓
「なぜ相性が良いか」を説明
        ↓
宣伝リスクを判定
        ↓
自然な英語返信案を作る
        ↓
人間が確認して投稿
```

## 主要ユースケース

### 1. 小説・Inkitt

英語版小説の読者候補や、執筆・公開・読者獲得について話しているスレを探す。

直接URLを貼ることを目的にせず、まず会話に価値を出せるスレを優先する。

### 2. 英語学習・教材

英語学習者が繰り返し困っていること、既存教材への不満、よく議論されている勉強法を抽出する。

教材制作・X投稿・授業テーマのネタとして使える。

### 3. アプリの需要調査

VOCADON、READON、Luckyなどのアイデアについて、Reddit上の生の悩み・不満・代替手段への要望を探す。

「似たアプリがあるか」だけでなく、「人が何に困っているか」を重視する。

### 4. 返信支援

URLまたは投稿内容から、次を作る。

- 投稿者の本当の質問
- 文脈要約
- 宣伝してよいか
- 宣伝するならどの程度まで自然か
- 英語返信案
- 宣伝なしの純粋な返信案

## 推奨出力

```text
🔴 92 / 100
r/writing
投稿タイトル

要約:
...

なぜチャンスか:
...

宣伝リスク: LOW / MEDIUM / HIGH
理由: ...

推奨行動:
1. まず質問に答える
2. 自分の経験を短く添える
3. 必要なら最後に作品やサービスへ触れる

英語返信案:
...

Reddit URL:
...
```

## ファイル構成

- [`SKILL.md`](./SKILL.md) — Reddit Radarの中核ワークフロー
- [`docs/QUICKSTART.md`](./docs/QUICKSTART.md) — ChatGPTからの使い方
- [`docs/SCORING.md`](./docs/SCORING.md) — Opportunity Scoreの基準
- [`docs/WORKFLOW.md`](./docs/WORKFLOW.md) — 検索から返信案までの手順
- [`docs/OUTPUT_FORMAT.md`](./docs/OUTPUT_FORMAT.md) — 出力形式
- [`docs/SAFETY.md`](./docs/SAFETY.md) — スパム防止・安全運用
- [`docs/DECISIONS.md`](./docs/DECISIONS.md) — APIアプリにしない等の設計判断
- [`docs/ROADMAP.md`](./docs/ROADMAP.md) — 将来拡張
- [`prompts/CHATGPT.md`](./prompts/CHATGPT.md) — ChatGPT用の短い実行指示
- [`projects/`](./projects) — 公開してよいProject profile
- [`projects/ZARIGANI.md`](./projects/ZARIGANI.md) — 英語版Web小説のRadar profile
- [`research/EXISTING_PROJECTS.md`](./research/EXISTING_PROJECTS.md) — RedSignal / Harken / RedoraAI / Devvit調査
- [`AGENTS.md`](./AGENTS.md) — Codex等がrepoを編集する際の制約
- [`CHANGELOG.md`](./CHANGELOG.md) — 変更履歴

## 現在の設計判断

当初はDevvit + OpenAI APIを使う独立アプリも検討したが、現段階では採用しない。

理由:

1. 普段のChatGPTだけで検索・分析・文章生成ができる。
2. APIキー管理を増やしたくない。
3. 追加課金を前提にしたくない。
4. 自動投稿より、人間が確認する運用の方がRedditに適している。
5. GitHubは「実行環境」ではなく「判断基準とワークフローの正本」として使う方がシンプル。

必要になった場合のみ、将来Devvit版を別ブランチまたは別ディレクトリで実装する。

## Public repository notice

このrepoはPublic。APIキー、OAuth token、Reddit cookie、password、生徒・顧客の個人情報などは保存しない。

## Status

**Phase 1: ChatGPT-first / Human-in-the-loop**

- [x] コンセプト定義
- [x] APIキー不要方針
- [x] 自動投稿をしない方針
- [x] Opportunity Score設計
- [x] 標準出力設計
- [x] 既存OSS調査
- [x] ChatGPT quickstart / canonical prompt
- [x] Project profile template
- [ ] 実際のReddit調査でスコア基準を調整
- [ ] 小説・英語学習・アプリ開発の3用途で実地テスト
