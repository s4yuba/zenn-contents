---
title: "2025年6月にClaude Codeが突然話題になった理由をまとめる"
emoji: "💡"
type: "idea"
topics:
  - "claude"
  - "anthropic"
  - "claudecode"
  - "claude4"
published: true
published_at: "2025-06-07 11:40"
---

:::message
この記事はAIによる誤字脱字の検出以外は人力で作成されました。
:::

Oikonです。外資IT企業でエンジニアをしています。

この記事は、𝕏（旧Twitter）でまとめた**Claude Codeが話題になっている理由**のポストを清書したものです。

後で見た時に懐かしむために、備忘録的にまとめます。

@[tweet](https://x.com/gaishi_narou/status/1928945837520073135)

## Claude Codeとは

Claude Codeの記事に興味を持って読みに来る人の多くは、現在のClaude Codeは何かをすでに知っていると思うので、少し過去に焦点を当てます。

* 2025年2月24日：**Claude Codeプレリリース（Research Preview版）**
* 2025年4月10日：**Claude Maxプランの登場（まだClaude Codeは入っていない）**
* 2025年5月1日：**Claude CodeがClaude Maxプランで定額使用可能に**
* 2025年5月22日：**Claude 4 (Opus/Sonnet）発表**

Claude Codeは2月にResearch Preview版がリリースされて一般でも使えるようになりました。

その際、使われていたのはClaude 3.7でCLIツールであることを除けば、基本機能は2025年6月現在のものと、さほど変わりありません。

この時点でも

* **コードベース全体の把握**
* **他のAIツール以上の自律駆動**
* **Claude 3.7の優秀なコーディング能力**

などの魅力はあり、一部では根強い人気がありました。

私も趣味の個人開発ではかなりお世話になっています。

5月1日にClaude MaxプランにClaude Codeが含まれてからは、API課金量を気にせずに使えるようになりました。

その頃はOpenAIのOpenAI o3やGoogleのGemini 2.5 ProといったAIが世間を賑わしていたため、そこまで注目している人は多くなかったように思えます。
                                                    
そんな中、**Anthropicの発表 (5月22日)で大きく変わりました**。

どんな発表があったかは以下のYoutubeで確認できます。

https://www.youtube.com/watch?v=EvtPBaaykdo&list=PLf2m23nhTg1P5BsOHUOXyQz5RhfUSSVUi&index=4

この記事では5月22日以降になぜClaude Codeに火がついたか、私の個人的な考えをまとめたいと思います。

## Claude Codeが話題になった理由

### ① Claude 4 (Opus/Sonnet)の性能が良い

![](https://storage.googleapis.com/zenn-user-upload/5c0f9d493b9b-20250604.png)

5月中旬までのClaude 3.7もコーディング能力は十分高かったです。

しかし、3月〜4月にかけてライバルのOpenAI o3とGemini 2.5 Proがリリースされ、Anthropicはリリーススピードで遅れをとった印象が否めなかったです。

そんな中でClaude 4 Opus/Sonnetがリリースされました。

ここでコケるとAI開発の競争からかなり遅れをとるところでしたが、Claude 4は多くの人の予想以上の性能を誇りました。

**2025年6月時点でおそらくコーディング能力は最強と言っても過言でないと思います。**

Claude 4の大幅な進歩によりエンジニア層を中心に大きな反響がありました。

### ② Claude MaxプランのClaude Code定額利用

![](https://storage.googleapis.com/zenn-user-upload/537bc5e35805-20250605.png)

もともとClaude Code自体は5月からClaude Maxプランの定額利用に含まれていました。

そのことはあまり知られていなかったのと、Claude 3.7の性能がどうしても他社の生成AIモデルに比べて見劣りするために利用者が少なかった印象です。

Claude 4シリーズがリリースされてからは性能面で評価され、Claude Code定額利用にも注目が集まりました。

それまではCursorやWindsurfといったAIエディタでの開発が主流でしたが、どうしてもAPI従量課金が気になって思い切った開発を行うことができなかった人も多かったです。

Claude Maxプランでは定額でClaude Codeを利用できるため、**API利用料を気にせずにAIによるTry & Errorを高速で回すことができるようになりました。**

このClaude Codeの定額利用も今までのAIサービスとの大きな違いとなり、注目される要素になったと思います。

### ③ VSCode, CursorなどのIDE統合

Claude CodeのIDE統合も注目された大きな要因でした。

もともとClaude CodeはCLIツールとしてプレリリースされていて、その時点でも優秀でした。

しかしCLIツールゆえに多くのエンジニアには刺さらなかった印象です。

5月22日の発表以降、以下のようなIDE統合ができるようになりました。

* **VSCode（CursorやWindsurfなどのフォークを含む）**
* **JetBrains IDE**

現在のエンジニアの多くは、これらのIDEで開発をしているため、**Claude Codeを今まで使っていたエディタに組み込むことができるようになったことで、ユーザーの裾野が一気に広がりました。**

以前にIDE統合についてのポストをした際も反響が大きかったです。

@[tweet](https://x.com/gaishi_narou/status/1926594846560764362)


### ④ 今まで以上のAI自律駆動

![](https://storage.googleapis.com/zenn-user-upload/8a0296a901ee-20250605.png)

Claude Codeの特徴として、タスクを任せたら自分でToDoリストを作り、自律的に遂行する点が挙げられます。

プロジェクト全体を理解した上でタスクを進められるのがClaude Codeの強みです。

これにより従来のAIモデルと比べて何が変わったかというと、**AIとの対話でコーディングをしていたところから、AIに仕事を任せる共同作業者に変わりました。**

AIに業務委託をする感覚に近くなったと思います。

明確に要件定義をして、ガードレールとしてのテストを用意することで、実作業部分をAIに任せることができるようになりました。

もちろん今はまだミスもありますが、Claude CodeはAIの自律駆動の可能性を見せてくれています。

開発者は手を動かしてコーディングの仕事をしていたところから、**要件定義と設計の上流工程にタスクが移動したと言えるでしょう。**

### 追加要素A： Claude Code GitHub Actions

Claude Code GitHub Actionsは5月22日に発表で一緒に発表された機能です。

GitHubのUI上で、Issue・Pull Requestに`@claude`をつけてタスクをお願いすると、GitHubの中で完全にタスクを完了してくれます。

一応こちらも話題にはなりましたが、Claude Maxプランでも関係なく従量課金での利用になります。

Claude Codeの盛り上がりに直接的に起因したかは、個人的には懐疑的なため追加要素としました。

### 追加要素B： GitHub Copilot

個人的に興味深い引用コメントもあったので共有します。

> 個人的には、6月からGitHub Copilotのプレミアムリクエスト数制の導入も大きい。

GitHub Copilotは（私の理解では）AIコーディングツールとして、ライトユーザから支持を集めていたと思います。

このCopilotが6月から実質的な制限のようなものを導入するため、ユーザーがCopilotからClaudeに流れたという意見もあり興味深かったです。

### 追記 （20250609)： Proプランの定額解放

書き忘れていた出来事がありました。

**2025年6月5日にClaude CodeがProプランにも定額解放されました**。

これによりMaxプラン($100〜)でなくともProプラン($20)でClaude Codeを試せるようになり、さらに利用者の裾野が広がったと思います。

さらに完全に余談ですが、6月2日のClaude Code v1.0.7の時点で **"Max or Pro"** の文言が存在していたため（すぐ消されました）、もともとProプランにも開放する予定だったのではないかと考えています。

@[tweet](https://x.com/gaishi_narou/status/1930552153338429858?s=46&t=EOzehqGDDoTIYPJgyz5jHA)


## まとめ： Claudeの時代が来た

個人的に、**Claude CodeはAI開発を一つ上のステージに進めたツールだと感じています。**

今後OpenAIやGoogleがこのコーディング領域に手を出すか不明ですが、Claude Code + Claude 4は間違いなくエポックメイキング的な出来事だったと思います。

Claude Codeの体験は、半年〜1年後以降のAI開発を先取りしていると私は考えています。

Anthropicファンとして、今後のClaudeの動向に注目していきたいです。

## 𝕏フォローしてくれると嬉しいです！

𝕏でも情報発信しているのでよかったらフォローしてくれると、とても励みになります！

https://x.com/oikon48

## 参考文献

* (20250225) [Claude 3.7 Sonnet and Claude Code](https://www.anthropic.com/news/claude-3-7-sonnet?utm_source=chatgpt.com)
* (20250410) [Introducing the Max Plan](https://www.anthropic.com/news/max-plan?utm_source=chatgpt.com)
* (20250523) [Introducing Claude 4](https://www.anthropic.com/news/claude-4?utm_source=chatgpt.com)