---
title: "【初心者向け】Claude Codeの脱初心者の考察"
emoji: "💡"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: [claudecode, claude, anthropic]
published: true
published_at: 2025-08-23 07:03
---

:::message
この記事は人力で書いています。
:::

Oikonです。外資企業でソフトウェアエンジニアをしています。

先日、何気なく以下のようなポストをしてみました：

https://x.com/oikon48/status/1958819935095820744

書いてあるように、Claude Code初心者向けに必要な情報を考える機会があり、その際に**Claude Codeの脱初心者について**気になりました。念のために補足すると、Claude CodeとはAnthropic社が提供しているAIコーディングツールです。

このことをX（旧Twitter）でポストしてみたところ、色々意見をいただいて個人的に気づきもあったので記事にしたくなりました。本当にそれだけの理由で書いているのでサラッと読み流してください笑

あと初心者の定義についてですが、正直SNS上の短いやり取りで設定を共有するのは難しいです。個人的には*コーディング経験が多少ありClaude Codeは初めての人*という想定でした。

## 現在のClaude Code

Claude Codeの脱初心者の話をする前に、**8月末時点でのClaude Codeについて私の個人的な認識を共有したいと思います**。

Claude Codeは5月末頃から急速にシェアを広げたAIコーディングツールです。なぜ話題になったかは以前に記事を書いているので、気になる方は読んでみてください。

https://zenn.dev/oikon/articles/adac12ea9e839b

AIコーディングツールはGitHub Copilot、Cursor、Windsurf、Gemini CLI、Codex CLI、Kiroなど、ここに挙げきれないくらい存在しています。その中でも**Claude Codeはモデルの性能に加え、コーディング性能の高さと定額で利用できることで人気**です。

Claude Codeにはさまざまな機能やTipsがあります。私がここでパッと思いつくキーワードを列挙しました。

* CLAUDE.md
* ultrathink
* スラッシュコマンド
* カスタムスラッシュコマンド
* MCPサーバー連携（これだけでもたくさん）
* Subagent
* Hooks
* Plan mode
* Opus Plan mode
* Claude Code GitHub Actions
* output-style
* statusline
* user/local settings
* claude -p (stateless call)
* --dangerously-skip-permissions
* allow/ask/deny
...

本当に思いついた順に挙げていきました。思いついてないだけでまだ機能はあります。

これだけ機能があり自由度が高いことが、Claude Codeが人気の理由になっている一つの要因だと思いますが、**初心者からすると難しいと感じる**人も多いようです。個人的に難しいと思われている理由としては以下が挙げられると思います。

* **コマンドが多い**
* **CLIツールである(黒い画面怖い)**
* **勝手に動いてファイルを全部消したりしそう**

これらは全部を習得する必要がなかったり、慣れで解決するものであったり、未然に防げたりするものばかりです。

そこで**初心者がまず目指すところはどこなのか**ということを考えた時に、さまざまな意見をいただきました。この記事ではいただいたコメントを紹介しつつ考察していきます。

## Claude Code脱初心者についての考察

ここからはXで頂いた意見を元に、脱初心者について考察していきます。

### ①カスタム Slash Commands を使いこなす

**カスタム Slash Commands が使えるようになったら脱初心者**という、私が元ポストで最初に話した脱初心者の考えです。今考えるとちょっとセンスがなかったと思います笑

ざっくりカスタム Slash Commands を説明すると、「あらかじめ記述した指示をコマンド一つで呼び出せる」機能です。

この機能は主に「よく使う指示をプロンプトにして使い回す」ことに使用できるため、指示の効率化が主な目的です。そのため慣れてきた初心者なら使いこなせると考えました。

**Slash Commands**:
https://docs.anthropic.com/en/docs/claude-code/slash-commands

### ②CLAUDE.mdのメンテナンスをする

https://x.com/kinopee_ai/status/1958822496532406393

**CLAUDE.mdのメンテナンス**についての意見をいただきました。

CLAUDE.mdはClaude Codeに読み込まれる永続コンテキストで、AIエージェントに前提として知っておいてほしいプロジェクトの情報やコーディングマナーなどについて記載します。

このCLAUDE.mdは初期設定の際に`/init`で作成することが多いのですが、開発が進むにつれてCLAUDE.mdの内容が風化することも多いです。

そのため、CLAUDE.mdのメンテナンスを定期的に行うことで、AIエージェントの指示を実際のプロジェクトに沿ったものに軌道修正する必要があります。コンテキストエンジニアリングの観点ではこの作業は非常に重要です。

このようにAIエージェントにインプットするコンテキストに気を配れると、脱初心者と言ってもいいのではないでしょうか。

**CLAUDE.md**:
https://docs.anthropic.com/en/docs/claude-code/memory

### ③`/clear` と `/compact` でコンテキストを整理をする

https://x.com/_nogu66/status/1958822216898150787

https://x.com/asahiXXXXXXXXX/status/1958833474976326133

**`/clear`と`/compact`でコンテキスト整理ができるようになる**という意見は2件いただきました。

それぞれの機能について説明すると、

* `/clear`: コンテキストウィンドウのリセット。新しいセッションを始める
* `/compact`: コンテキストウィンドウを要約して、新しいセッションに一部引き継ぐ

これらも前述のCLAUDE.mdと同じように、AIエージェントのコンテキストを気にすることができることが重要視されています。

それぞれの機能は前述の[Slash Commands](https://docs.anthropic.com/en/docs/claude-code/slash-commands)のドキュメントに記載されています。

### ④そもそもAIツールを使い続けられる

https://x.com/m2ai_jp/status/1958820282292216108

これには個人的にハッとさせられました。

もともとの議論はClaude Codeの脱初心者だったのは事実ですが、**そもそもClaude Codeに手を出している時点で世の中の多くのエンジニアよりもAIツールに明るいのです**。その時点で脱初心者と言われてもいいのではないでしょうか。

AIツールを理解するのも大事ですが、そもそもAIツールを使えるということも大事だと思います。

## まとめ

今回は**Claude Codeの脱初心者**という取り留めのないトピックでしたが、個人的に色々と考えさせられました。

改めて元ポストを貼ります。他にもいくつか面白い意見をいただいているので、良かったら眺めてみてください。

https://x.com/oikon48/status/1958819935095820744

真面目に脱初心者の基準を考えるなら、**コンテキストに気を配れるか**というのが私の結論になりました。ただこのコンテキストエンジニアリングも、半年後にはおそらく状況が変わっていると思っています。

では今何ができるかについて、私の考えを伝えます。

**Claude Codeを最近使い始めた人は、その調子でどんどん使ってAIコーディングに慣れていってください。AIツールは使わなければ見えてこないものがあります。**。

**Claude Codeを使ったことがない人はまず使ってみましょう。以下にコマンドを置いておきます**。

```bash
npm install -g @anthropic-ai/claude-code
```

**Set up**:
https://docs.anthropic.com/en/docs/claude-code/setup

AIコーディングは、まずはとにかく慣れていくことが一番大事だと思っています。使っていくにつれて脱初心者を達成できるはずですので、日頃からAIツールと共に過ごす時間を増やしましょう。

## 𝕏フォローしてくれると嬉しいです！

𝕏でも情報発信しているので、フォローしていただけると励みになります！

https://x.com/oikon48

## 参考文献

* [Slash Commands - Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code/slash-commands)

* [Memory (CLAUDE.md) - Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code/memory)

* [Set up - Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code/setup)
