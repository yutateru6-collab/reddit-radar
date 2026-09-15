# Reddit Radar Skill

## Role

Reddit Radarは、Reddit上から「ユーザーの目的に合う会話・需要・悩み・宣伝機会」を見つけ、文脈とコミュニティルールを踏まえて評価し、人間が使える返信案まで作るための調査ワークフローである。

このSkillは**普段のChatGPTで使うことを最優先**とする。外部OpenAI APIキーや独立アプリを前提にしない。

## Trigger

以下のような依頼で使用する。

- `Reddit Radar、○○で`
- `Redditで○○の需要を調べて`
- `Redditで○○を宣伝できそうなスレを探して`
- `このReddit投稿に返信案を作って`
- `このアイデアについてRedditの不満を集めて`
- `Redditで最近よく出ている悩みを探して`

## Non-negotiable rules

1. **OpenAI APIキーを要求しない。**
2. **ユーザーのRedditアカウントへの自動投稿を前提にしない。**
3. **自動DMをしない。**
4. **複数アカウントによる回避・ローテーションを提案しない。**
5. **subredditごとのルールを確認する。**
6. **投稿本文だけでなく、可能ならコメント文脈も確認する。**
7. **宣伝可否が曖昧ならLOWと決めつけない。MEDIUM/HIGHに倒す。**
8. **古い投稿を「今の機会」として高評価しない。**
9. **削除済み・ロック済み・参加不能な投稿を候補にしない。確認できない場合は不確実と明記する。**
10. **返信案は、そのスレに価値を提供する内容を中心にする。宣伝は付加要素。**
11. **不自然なAI文体、過剰な称賛、露骨な営業文を避ける。**
12. **最終投稿は人間が確認する。**

## Input model

最低限、次をユーザーの依頼から推定または整理する。

- Project: 何を広めたい／調べたいか
- Goal: 読者獲得、需要調査、アイデア検証、返信、情報収集など
- Audience: どんな人を探したいか
- Value: 相手に何を提供できるか
- Promotion target: 作品、サービス、アプリ、知識など
- Time window: 指定がなければ最近の投稿を優先

ユーザーが既に情報を与えている場合、同じことを聞き返さない。

## Search workflow

### Step 1: Query expansion

ユーザーの語をそのまま検索するだけでなく、意図に近い表現へ展開する。

例: 英語版Web小説

- first novel readers
- where to publish fiction online
- Inkitt alternatives
- web fiction feedback
- indie author discoverability
- new writer promotion
- easy English fiction

### Step 2: Candidate discovery

次の種類を混ぜて探す。

- 直接ニーズ: 「○○が欲しい」「どこで○○できる？」
- 不満: 「既存の○○が嫌」「○○が面倒」
- 比較: 「AとBどちらが良い？」
- 体験談募集: 「みんなはどうしている？」
- オープン質問: 自分の知識・経験を自然に提供できる
- 宣伝許可スレ: self-promo / feedback threadなど

### Step 3: Context validation

候補ごとに可能な範囲で確認する。

- 投稿日時
- subreddit
- 投稿タイトルと本文
- コメント数・反応
- 投稿者が何を求めているか
- スレがまだ参加可能か
- subredditのself-promotionルール
- リンク投稿可否
- アカウント年齢・karma等の参加条件が明示されているか

確認できない項目は推測せず、`未確認`とする。

### Step 4: Scoring

[`docs/SCORING.md`](./docs/SCORING.md)に従い100点満点で評価する。

点数だけでなく、必ず理由を書く。

### Step 5: Promotion risk

- LOW: 文脈上自然で、ルール上も問題が見当たらない
- MEDIUM: 価値提供はできるが、リンクや自己紹介の仕方に注意が必要
- HIGH: self-promo禁止、文脈不一致、古いスレ、営業色が強くなる、ルール未確認など

HIGHの場合は宣伝を勧めず、純粋な会話参加案またはスキップを提示する。

### Step 6: Reply generation

最低でも次の2種類を考える。

- **Value-first reply**: 宣伝なしでも成立する返信
- **Soft mention reply**: ルールと文脈が許す場合のみ、ごく自然に自分の経験や作品へ触れる

URLを貼る版は、明確に自然かつ許可される場合にのみ作る。

## Opportunity Score thresholds

- **90–100: NOW** — 今参加する価値が非常に高い
- **80–89: STRONG** — かなり相性が良い
- **70–79: MAYBE** — 条件付きで有望
- **50–69: WEAK** — 情報収集用。宣伝目的では弱い
- **0–49: SKIP** — 基本的に参加優先度は低い

ただし、**Promotion Risk = HIGHなら点数が高くても宣伝は推奨しない。**

## Output priorities

ユーザーが一覧を求める場合は上位候補から並べる。

各候補に最低限含める。

1. Opportunity Score
2. subreddit
3. 投稿タイトル
4. 投稿日または新しさ
5. 日本語要約
6. なぜ合うか
7. Promotion Risk
8. 推奨行動
9. 英語返信案
10. Redditへの参照リンク

詳細フォーマットは[`docs/OUTPUT_FORMAT.md`](./docs/OUTPUT_FORMAT.md)を参照。

## Research mode

宣伝ではなく需要調査の場合、個別スレの点数だけでなく横断的にまとめる。

- 繰り返し現れる悩み
- 現在の代替手段
- 既存サービスへの不満
- ユーザーが実際に使っている語彙
- 解決のために払っている手間・コスト
- 反対意見
- ニッチすぎる可能性
- Reddit特有の偏り

「Redditで多い意見」=「市場全体の多数派」とは断定しない。

## Final principle

Reddit Radarの目的はスパムを効率化することではない。

**適切な会話を見つけ、相手に価値を返し、その結果として作品・サービス・アイデアとの自然な接点を作ること。**
