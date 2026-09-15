# Roadmap

## Phase 1 — ChatGPT-first

目的: APIキーなしで価値を検証する。

### 完了済み

- Reddit Radarのコンセプト定義
- ChatGPT内で使う方針へ変更
- OpenAI APIキー不要
- 自動投稿なし
- Opportunity Score 100点設計
- Promotion Risk設計
- 標準出力設計
- 市場調査モード設計
- 既存OSS調査

### 実地検証

次の3用途で実際に使う。

1. 英語版小説 / Inkitt
2. 英語学習・教材・VOCADON系
3. 新規アプリの需要調査

検証項目:

- 上位候補が本当に返信したくなるスレか
- Scoreと人間の直感が一致するか
- Promotion Riskが甘すぎないか
- Redditの検索漏れがどの程度あるか
- 返信案が自然か

## Phase 1.5 — 定期Radar

ChatGPTのスケジュール機能等で、必要なテーマを定期的にチェックする。

例:

- 毎朝: web fiction / indie author関連
- 週2回: vocabulary learning / English learning pain points
- 週1回: 新しい教育アプリ需要

通知条件は「新しい高得点候補があるときのみ」を基本とする。

## Phase 2 — Tracking

手動で反応データを記録する。

候補データ:

- date
- subreddit
- URL
- score
- promotion risk
- action
- result
- upvotes
- replies
- removed / not removed
- learning

目的は、Opportunity Scoreを実データで改善すること。

## Phase 3 — Multi-source Radar

Redditで価値が確認できたら、必要に応じて他ソースへ広げる。

候補:

- Hacker News
- Bluesky
- Stack Overflow
- YouTube comments/search
- RSS

Harkenのようなsocial listening設計を参考にする。

## Phase 4 — Optional App

大量の候補管理が本当に必要になった場合のみWebアプリ化を検討。

候補:

- Reddit Devvit Web
- local/self-hosted dashboard
- SQLite
- saved projects
- watch lists

ただし以下は維持する。

- 人間確認
- 自動大量投稿をしない
- ban回避設計をしない
- APIキー必須にしない方法を優先

## Not planned by default

- autonomous Reddit marketing bot
- automatic DMs
- automatic cold outreach
- account rotation
- karma farming
- mass reply generation and posting

これらはReddit Radarの中心機能にしない。
