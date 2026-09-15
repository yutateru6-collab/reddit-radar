# Workflow

## 0. 目的を1行で固定する

調査前に、今回のゴールを1行で定義する。

例:

- `英語版Web小説の読者候補がいる会話を探す`
- `英語学習アプリに対する不満を集める`
- `単語学習アプリを自然に紹介できる会話を探す`

目的が複数ある場合は、宣伝・需要調査・返信支援を混ぜず、結果を分けて扱う。

## 1. Query Expansion

検索語を4種類に広げる。

### A. Product words

対象そのもの。

例: `Inkitt`, `web fiction`, `vocabulary app`

### B. Problem words

悩みを表す言葉。

例: `can't find readers`, `forget vocabulary`, `hard to stay motivated`

### C. Intent words

行動意図。

例: `recommend`, `looking for`, `how do you`, `what do you use`, `alternatives`

### D. Adjacent words

本人が対象名を知らなくても、同じ問題を抱える表現。

例: `first novel`, `indie author`, `reading practice`, `study streak`

## 2. Discovery

最低でも複数の検索角度から候補を集める。

優先順位:

1. 最新の直接ニーズ
2. 最新の不満・困りごと
3. 推薦募集
4. 比較相談
5. 活発な一般議論
6. 過去の有用スレ（市場調査用）

宣伝目的の場合、古い高評価スレより新しい中規模スレを優先することがある。

## 3. Verify the actual thread

検索結果のスニペットだけで判定しない。

可能な範囲で実際の投稿ページを確認する。

見る項目:

- タイトル
- 本文
- 投稿日
- subreddit
- コメント数
- 上位コメント
- 投稿者が追加説明していないか
- ロック・削除状態
- すでに同じ商品や作品が大量に宣伝されていないか

## 4. Check community rules

宣伝を含む可能性がある場合は特に重要。

確認対象:

- self-promotion
- external links
- surveys / research
- AI-generated content
- solicitation
- weekly promo threads
- karma / account age requirements

ルールが確認できない場合は、その事実を結果に残す。

## 5. Score independently

[`SCORING.md`](./SCORING.md)の各項目を別々に採点する。

悪い例:

`なんとなく良さそうなので92点`

良い例:

```text
Intent Match 23/25
Recency 15/15
Conversation Openness 14/15
Value Fit 18/20
Promotion Compatibility 10/15
Engagement Potential 8/10
Total 88/100
```

## 6. Challenge the recommendation

高得点候補ほど、逆に「やめた方がよい理由」を探す。

チェック:

- 宣伝したい気持ちで関連性を過大評価していないか
- 投稿者は本当に推薦を求めているか
- 既存コメントですでに解決していないか
- subreddit文化に合うか
- 返信が自分語りになっていないか
- リンクを貼る必要が本当にあるか

## 7. Decide action

候補ごとに次のどれかを選ぶ。

- `REPLY NOW`
- `REPLY WITHOUT PROMOTION`
- `SOFT MENTION ONLY`
- `WATCH`
- `RESEARCH ONLY`
- `SKIP`

## 8. Draft reply

返信は原則として次の順序。

```text
相手の質問への直接回答
↓
具体的な経験・役立つ情報
↓
必要なら補足
↓
文脈上自然な場合のみsoft mention
```

宣伝対象へのリンクは最後の手段。

## 9. Human review

投稿前に人間が確認する。

確認ポイント:

- 本当に自分が言いそうな文か
- 事実に誤りがないか
- 自分の経験として書いてよい内容か
- AIが存在しない経験を捏造していないか
- URLを貼る必要があるか
- subredditルールに反していないか

## 10. Learn from results

実際に返信した場合、可能なら後から結果を記録する。

- 返信日時
- score
- upvote / reply
- 削除されたか
- 自然な会話になったか
- 作品・サービスへの流入があったか

十分な実績がたまったらScoringの重みを調整する。
