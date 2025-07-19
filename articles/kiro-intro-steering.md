---
title: "KiroのAgent Steeringの概念が良いという話"
emoji: "💫"
type: "tech"
topics: [kiro, aws, ai, ide]
published: false
---

:::message
この記事は人力で書かれています。
:::

Oikonです。外資でエンジニアしています。

2025年7月15日(火)に、AWSがAIエディタ**Kiro Preview版**をリリースしました。

Kiroの基本思想は**仕様駆動開発（Spec-driven Development）**です。

1. **要件定義（Requirements）**
2. **技術設計（Design）**
3. **タスク実行（Tasks）**

この3つをSpecsで設定して開発していく流れになっています。Kiroはそれぞれについてドキュメントを生成して、専用のUIも提供しています。

![kiro-intro-steering](/images/kiro-intro-steering/kiro-intro-steering.png)

この仕様駆動開発は、Specで用意された3つのドキュメントを使用して開発を行なっていきます。

この記事では、この仕様駆動開発を裏側で支える**Agent Steering**について紹介したいと思います。現在あまり注目されていませんが、今後のAIエージェントによる開発のやり方に**Kiro**はヒントを与えてくれました。

:::message
ちなみに記事執筆時には[KiroはWaitlist待ち](https://kiro.dev/)になっていますが、Homebrewでインストールもできるそうです。

```sh
brew install --cask kiro
```

:::

## KiroのAgent Steering

https://kiro.dev/docs/steering/index

### Agent Steering 概要

Agent Steeringは、`.kiro/steering/`以下のMarkdownファイルを通じて、Kiroにプロジェクトに関する永続コンテキストを提供するものです。Claude Codeの`claude.md`やGemini CLIの`gemini.md`みたいなものという認識です。

### UI

![kiro-intro-steering2](/images/kiro-intro-steering/kiro-intro-steering2.png)

KiroのAgent Steeringは画像のように、IDEのKiroタブの3つ目に存在します。デフォルトではSteeringのドキュメントは存在しません。

### Steering file

**Generate Steering Docs**を押すことで、Kiroが以下の3つのSteeringファイルを作成してくれます。

- `product.md`: **製品概要**。製品について、ターゲット、主機能、ビジネス目標を定義します。
- `tech.md`: **技術スタック**。フレームワーク、ライブラリ、開発ツール、および技術制約を文書化します。
- `structure.md`: **プロジェクト構造**。ファイル構成、命名規則、アーキテクチャ上の決定事項を概説します。

ちなみに後述するカスタムSteeringファイルを作成していても、コマンドパレット(`command+shift+p`)から3つのデフォルトドキュメントは生成できます。

Kiro: Generate project steering documents:

![kiro-intro-steering3](/images/kiro-intro-steering/kiro-intro-steering3.png)

Generate Steering Docsを実行すると以下の画像のように、Kiroが3つのSteeringドキュメントを`.kiro/steering/`に作成します。

![kiro-intro-steering5](/images/kiro-intro-steering/kiro-intro-steering5.png)

KiroはSteeringファイルを作成する際には、既存のプロジェクトの構造や設定ファイルをチェックしていることが分かります。

### Custom Steering file

デフォルトで作成するSteeringファイルの他に、ユーザー独自の**Custom Steering file**を作成することもできます。

- Agent Steering Viewで`+`ボタンを押す
- コマンドパレットで`Kiro: Generate a custom steering file`

上記2つの方法で作成できます。

たとえば例として以下のようなカスタムSteeringファイルを作成すると、仕様書などを日本語で作成してくれるようになります。

```md:.kiro/steering/guidelines.md
---
inclusion: always
---

# Guidelines

## Documentation Standards

### Spec Planning Documents
- Generate/Update `requirements.md` in Japanese
- Generate/Update `design.md` in Japanese
- Generate/Update `tasks.md` in Japanese

### Steering Documents
- Generate/Update `product.md` in Japanese
- Generate/Update `tech.md` in Japanese
- Generate/Update `structure.md` in Japanese
```

英語で記述していますが、おそらく日本語でも効くはず。

### Steering fileの適用範囲

Steeringファイルは、ファイル先頭にオプションをつけることで適用範囲を制限できます。公式ドキュメントを尊重してyamlで書いていますが、mdファイルに追加して構いません。

- 常に読み込む（デフォルト）：

```yaml
---
inclusion: always
---
```

- 条件付きで読み込む：

```yaml
---
inclusion: fileMatch
fileMatchPattern: "components/**/*.tsx"
---
```

- 手動で読み込む

```yaml
---
inclusion: manual
---
```

手動で読み込む際は、プロンプトに`#steering-file-name.md`を指定してあげれば読み込んでくれます。

個人的に**柔軟に永続コンテキストを与えられるという点が良い**と感じました。この点については後述します

### Steering関係のコマンド

KiroのSteering関係のコマンドは、以下のようなものがあります。

![kiro-intro-steering4](/images/kiro-intro-steering/kiro-intro-steering4.png)

今まで取り上げてなかったものとしては、`Kiro: Refine this Steering document`があります。

これはKiroのエディタで開いているSteeringドキュメントを、Kiroがアップデートしてくれるコマンドです。

## KiroのAgent Steeringの何がいいか

ここからKiroのAgent Steeringの良い点について自分なりに考察していきます。

- 必須コンテキストの提案
- コンテキストの分割による管理の容易さ
- コンテキストの適用範囲の柔軟性

上記3つについて、それぞれ考えを紹介します。

### 必須コンテキストの提案

まず最初にKiroを使った時に思ったことは、「これClaude Codeの`claude.md`と同じか？」という感想でした。

念の為`claude.md`について補足しておくと、`claude.md`はClaude Codeに常に渡されるコンテキストです。主に「プロジェクト概要」「構造」「技術スタック」「ルール」などを記載することが多いです。

実際、Kiroで生成される3つのSteeringファイル（`product.md`、`tech.md`、`structure.md`）は、`claude.md`に記載するような内容が書かれています。

`claude.md`も`/init`でデフォルトファイルを作成してくれますが、プロジェクトによって毎回内容が違うことも多いです。

Kiroは3つのSteeringファイルを通して、**「製品概要」「技術スタック」「プロジェクト構造」がAIエージェントのコーディングに必要というAWSの考えを示してくれた**ことが個人的に良いと思いました。

### コンテキストの分割による管理の容易さ

KiroはSteeringファイルによって、今まで`claude.md`のように1つのファイルで与えていたコンテキストを分割化できるようになりました。

これには以下のメリットがあると考えられます：

- ドメインによるコンテキストの分割
- 永続コンテキストのメンテナンス性の向上
- AIエージェントへのコンテキストの明示

1つのファイルによる永続コンテキスト管理は限界を個人的に感じることが最近は多いです。また1つのファイルに複数の指示を記載すると、そのプロジェクトのみにしか適用できないドキュメントになります。

Steeringファイルによるコンテキストの分割は、**ドメインごとに管理しやすくする良い手法**だと感じました。

実際に公式ドキュメントでもドメインごとにSteeringファイルを分けるように伝えています。

> **Keep Files Focused** One domain per file - API design, testing, or deployment procedures.

(**焦点を当てる** 1つのファイルあたり1つのドメイン - APIデザイン、テスト、デプロイ手順)

典型的な例も引用しておきます。

> ## Common Steering File Strategies
>
> **API Standards** (`api-standards.md`) - Define REST conventions, error response formats, authentication flows, and versioning strategies. Include endpoint naming patterns, HTTP status code usage, and request/response examples.
>
> **Testing Approach** (`testing-standards.md`) - Establish unit test patterns, integration test strategies, mocking approaches, and coverage expectations. Document preferred testing libraries, assertion styles, and test file organization.
>
> **Code Style** (`code-conventions.md`) - Specify naming patterns, file organization, import ordering, and architectural decisions. Include examples of preferred code structures, component patterns, and anti-patterns to avoid.
>
> **Security Guidelines** (`security-policies.md`) - Document authentication requirements, data validation rules, input sanitization standards, and vulnerability prevention measures. Include secure coding practices specific to your application.
>
> **Deployment Process** (`deployment-workflow.md`) - Outline build procedures, environment configurations, deployment steps, and rollback strategies. Include CI/CD pipeline details and environment-specific requirements.

### コンテキストの適用範囲の柔軟性

KiroのSteeringファイルについて良いと思ったのは、コンテキストの適用範囲を調整できる点です。

```yaml
---
inclusion: fileMatch
fileMatchPattern: "components/**/*.tsx"
---
```

前述したように、`inclusion`を調整することで、全てのSteeringファイルを読みこむ必要がなくなりました。

今までは`claude.md`で1つの大きな永続コンテキストを渡していたのに対して、**不必要なコンテキストを渡さず、コンテキストウィンドウを汚染しないアプローチを取ることができます**。

最近話題になっているコンテキストエンジニアリングの観点からも、今までより良い柔軟なコンテキストの渡し方ができるようになっています。

## なぜAgent Steeringがそこまで話題になっていないか

ここまでKiroのAgent Steeringは良いよと言ってきましたが、Kiroのユーザーを見ているとそこまで注目されていません。

それはなぜかというと、**Kiroのコーディングエージェントの実装力と安定性が弱いから**だと思います。

現在KiroはPreview版のため、使用できるAIモデルは**Claude Sonnet 4**もしくは**Claude Sonnet 3.7**に限定されています。

Claude Opus 4などの実装力に比べると実装力に物足りなさを感じるユーザーも多いです。

またKiro Preview版は無料で使用できるため、現在混雑しており、**Claude Sonnet 4にするとAIエージェントが落ちる**ことがしばしばあります。

@[tweet](https://x.com/gaishi_narou/status/1945678342390169859)

これらの背景から、Kiroには設計のみ任せて、Claude Codeに実装してもらうユーザーが多いようです。

https://zenn.dev/ubie_dev/articles/kiro-claude-code

個人的にこの流れは仕方がないと思っていますが、**今後Kiroが安定してClaude Codeのような高性能AIモデルを使えるようになった際には、このAgent Steeringの仕組みは活きるようになる**と考えています。

## まとめ

この記事ではAWSのAIエディタ「Kiro」のSteering Agentについて紹介しました。

個人的にAIエージェントにコンテキストを渡す仕組みについて良いヒントをもらいました。

- 必須コンテキストの提案
- コンテキストの分割による管理の容易さ
- コンテキストの適用範囲の柔軟性

そのうちClaude CodeなどでもKiroのようなAgent Steeringが実装されてもおかしくないと思っています。

AWSのサービスと共に提供できるKiroは、今後も伸びていく可能性が高いと思うので、一度触ってみることをオススメします。

## 参考文献

https://kiro.dev/

https://kiro.dev/blog/introducing-kiro/

https://kiro.dev/docs/steering/index

https://zenn.dev/ubie_dev/articles/kiro-claude-code
