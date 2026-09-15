# Output Format

Reddit Radarの回答は、目的に応じて以下の形式を使う。

## A. Opportunity Radar

宣伝・会話参加候補を探すときの標準形式。

```text
REDDIT RADAR
Project: <project>
Goal: <goal>
Checked: <date/time or search window>

#1  92/100 — NOW
r/<subreddit>
<title>

投稿日: ...
状態: 参加可能 / 未確認 / ロック等

日本語要約:
...

投稿者が求めていること:
...

なぜ相性が良いか:
...

Score:
Intent Match            24/25
Recency                 15/15
Conversation Openness   14/15
Value Fit               19/20
Promotion Compatibility 12/15
Engagement Potential     8/10
Total                    92/100

Promotion Risk: LOW / MEDIUM / HIGH
理由: ...

推奨行動: REPLY NOW / REPLY WITHOUT PROMOTION / SOFT MENTION ONLY / WATCH / SKIP

英語返信案:
...

必要ならsoft mention版:
...

Reddit:
<reference>
```

## B. Quick Radar

ユーザーが簡潔な結果を求める場合。

```text
1. 92点 | r/writing | LOW
   「...」
   → 今返信する価値が高い。理由: ...

2. 84点 | r/selfpublish | MEDIUM
   「...」
   → 返信は有望。ただしリンクは貼らない方がよい。
```

上位3〜10件を基本とする。候補が弱い場合は無理に件数を埋めない。

## C. Market Research

需要調査・アイデア検証の場合。

```text
REDDIT MARKET RADAR
Topic: ...

繰り返し出ている悩み
1. ...
2. ...
3. ...

現在使われている代替手段
- ...

不満
- ...

ユーザーが実際に使っている表現
- "..."

反対証拠 / 需要が弱い可能性
- ...

示唆
- ...

確信度:
HIGH / MEDIUM / LOW

注意:
Reddit上の観測であり、市場全体を代表するとは限らない。
```

## D. Single Thread Analysis

URLを1件渡された場合。

```text
結論:
このスレでは <宣伝してよい / soft mentionのみ / 宣伝しない> を推奨。

Opportunity Score: 82/100
Promotion Risk: MEDIUM

投稿者の本当の質問:
...

注意点:
...

おすすめ返信:
...

宣伝なし版:
...

soft mention版:
...
```

## E. Reply Options

返信文を複数作る場合は、差を明確にする。

- Natural — 最も普通で自然
- Helpful — 情報量多め
- Short — Redditらしく短い

同じ文章を語尾だけ変えた3案にはしない。

## Language

分析・説明は原則日本語。

Reddit投稿用の返信案は、対象スレの言語に合わせる。英語スレなら自然な英語にする。

英語返信案では、AIっぽい以下の癖を避ける。

- 過剰なダッシュ
- `It's worth noting that...` の連発
- 不必要な箇条書き
- 相手を大げさに褒める導入
- 長すぎる結論
- 営業コピーのようなCTA

## Citation / evidence

検索・調査結果を示すときは、ユーザーが元スレを確認できる参照を付ける。

事実と推測を区別し、確認できなかったルール・状態・投稿日などは明記する。
