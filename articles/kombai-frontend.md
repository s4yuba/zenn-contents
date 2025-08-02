---
title: "Figma to CodeのAIツール「Kombai」を使ってみた"
emoji: "🐕"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [kombai, ai, frontend, css]
published: true
published_at: 2025-08-02 18:06
---

:::message
この記事でAIは誤字脱字の検出のために使用しています
:::

Oikonです。

今回は**Figma to CodeのフロントエンドAIツールのKombai**を使ってみたので紹介します。

Kombaiは[Product Hunt](https://www.producthunt.com/products/kombai)で過去に１位を獲ったことがあり、2025年7月31日にリリースされました。

https://x.com/gaishi_narou/status/1950938306025320682

個人的な総評としては以下のとおりです

- **VSCodeやCursorのプラグインとして使いやすい**
- **SandboxでUIが確認できるのがとても良い**
- **UIのコンパイル成功率が高めなのが結構えらい**
- **Figma to CodeはPixel Perfectではないが、叩き台としては優秀**

Claude CodeなどのAIコーディングツールは、フロントエンドやUIのコーディングが苦手な印象があるので、フロントエンド特化のAIは個人的に興味深いです。

## Kombaiについて

https://kombai.com/

Kombaiは、フロントエンド開発に特化したAIエージェントであり、AIによる開発支援ツールとして注目されています。2023年にはProduct Huntの最もUpvoteされたツールとして選ばれました([link](https://www.producthunt.com/products/kombai))。Kombaiはフロントエンド開発のAI自動化を目指しています。

> At Kombai are building a developer tool for web app developers which takes away their mundane automatable tasks like writing and maintaining CSS and other boilerplate JS code. Our vision is to automate all the mundane tasks a frontend dev team has to do today, accounting for 60-70% of their work.

[製品ページ](https://kombai.com/)ではフロントエンド開発についてのベンチマークが公開されています。Code Review、Featureの実装、コンパイル成功の3つにおいて、Kombaiは一般的に使用されているAIコーディングエージェントよりも良い性能を出していると報告しています。

![benchi](/images/kombai-frontend/benchi.png)

価格はFreeプランからあり、クレジットが付与されます。後述しますが、**Figma一つ読み込んでUIを作るのに大体20 ~ 40クレジット**でした。

![price](/images/kombai-frontend/pricing.png)

## Kombaiを使ってみる

### インストール

Kombaiは現在以下のマーケットプレイスで公開されています

- VSCode
- Cursor
- Windsurf

今回はCursorにKombaiをインストールする流れを説明します。

プラグインの検索に”Kombai”を入力すると、犬のアイコンのKombaiが表示されます。

![install](/images/kombai-frontend/install.png)

インストールすると`Sign in`の画面がエディタのViewに表示されます。アカウントを作成していない場合は`Sign up`を選択します。

![signin](/images/kombai-frontend/signin.png =400x)

サインインに成功すると以下のような画面になります。
![signin-success](/images/kombai-frontend/signin-success.png =400x)

### 自然言語でUIを作成

まず自然言語でUIの作成を指示してみました。以下のプロンプトを入力しています。

```chat
ポケモン図鑑を作りたい。第一世代の151匹まで全て見れるようにする。
```

![demo1-0](/images/kombai-frontend/demo1-0.png)

チャットを実行すると、どのような技術スタックを使用してフロントエンドを設計するかリストされます。

![demo1-1](/images/kombai-frontend/demo1-1.png)

- フレームワーク: React 19 TypeScript
- APIフレームワーク: RTK, RTK Query
- ルーター: React Router v7 (declarative mode)
- コンポーネントライブラリ: MUI v7
- スタイル: Emotion

技術スタックの選択肢として提供されているものは日本で好まれているものと少し違う印象です。必要に応じて`Configure stack`から使用する技術スタックを変更できます。

![demo1-2](/images/kombai-frontend/demo1-2.png)

項目としては以下のようなものがあります:

- Framework
- API & State Management
- Router
- Components
- Styling
- Icons
- Global Instructions
- Advanced Configurations

詳しい技術スタックは以下のドキュメントに載っています

https://docs.kombai.com/core-features/configure-tech-stack

技術スタックを決定したら、Planning Phaseに移行します。Planning PhaseではどのようなViewやコンポーネントを作成するかリストしてくれます。問題があれば編集したり口を出したりすることも可能です。

![demo1-5](/images/kombai-frontend/demo1-5.png)

Planning Phaseの内容に問題がなければ実行します。実行が終わると以下の画像のように、`Run in Sandbox`というボタンが表示されます。

![demo1-6](/images/kombai-frontend/demo1-6.png)

`Run in Sandbox`を実行すると、localhostで実際に作成したフロントエンドを表示・操作することが可能です。**Sandbox内でAIが生成したフロントエンドの確認ができる点が、Kombaiの強み**だと思います。

![demo1-7](/images/kombai-frontend/demo1-7.png)

今回作成してもらったポケモン図鑑は以下です。MUIっぽいUIですね。

![demo1-8](/images/kombai-frontend/demo1-8.png)

5つのMockデータを用意してくれました。

試しに追加で以下のプロンプトを追加指示してみました。

```chat
ポケモンを151種類にして。あとUIの言語は全て日本語で。
```

追加指示によって生成されたポケモン図鑑は以下の画像です。ちゃんと日本語対応と151種のMockデータが用意されました。

![demo1-9](/images/kombai-frontend/demo1-9.png)

Sandbox内ではUI操作も可能でした。例えばポケモンを選択すると、個別のポケモンの詳細を確認できました。

![demo1-10](/images/kombai-frontend/demo1-10.png)

これ以外にも**検索やフィルターも正しく使用できることをSandbox内で確認できました**。

Sandbox内の変更に問題がなければ、変更を保存できます。逆に言うと変更を採用しない限りKombaiはローカルの作業環境に変更を反映しません。Sandbox内で開発したものは、チャット内のチェックポイントまでRestoreも可能です。

![restore](/images/kombai-frontend/restore.png)

今回のポケモン図鑑のフロントエンド生成物は以下のとおりです。

![demo1-11](/images/kombai-frontend/demo1-11.png)

Kombaiはコンポーネントの作成だけでなくフロントエンドのフォルダ分けもしてくれました。

### FigmaからUIを作成する

KombaiはFigmaを取り込んでUIにする「Figma to UI」の機能も提供しています。チャットの右下の`Add Figma link`から追加できます

![figma-link](/images/kombai-frontend/figma-link.png)

Figma URL入力用のダイアログが表示されます。Figma URLの取得の仕方もDialogに書いてあります。

```sh
フレームを右クリック > "Copy/Paste as" > "Copy link to selection"
```

初回はFigmaとKombaiを繋ぐ認証が必要になります。

![figma-url](/images/kombai-frontend/figma-url.png =600x)

Figma URLが正しく読み込まれると以下の画像のように、Figmaのデザインがプロンプトに表示されます。このデザインは`@`のリソース扱いなので、複数のFigmaデザインを読み込むことも可能でした。

![figma-view](/images/kombai-frontend/figma-view.png)

実際にいくつかFigmaのデザインからUIを作らせてみたものを紹介します。参考までに全てOne-shot Promptです。

例を3つ紹介するので、**FigmaデザインとKombaiの生成物を見比べてみてください**。ちなみに１つあたり、20 ~ 40クレジットほど消費しました。

#### 例1

**Figmaデザイン**([link](https://www.figma.com/community/file/1252561852327562039)):
![figma-1](/images/kombai-frontend/figma-1.png)

**Kombaiの生成物**:
![example-1](/images/kombai-frontend/example-1.png)

#### 例2

**Figmaデザイン**([link](https://www.figma.com/design/eaY2PdzUqfFrSlkHBd3j0e/Stock-Portfolio-Dashboard--Community-?node-id=0-1&p=f&t=QYKekSD0zUGvLPZK-0)):
![figma-2](/images/kombai-frontend/figma-2.png)

**Kombaiの生成物**:
![example-2](/images/kombai-frontend/example-2.png)

#### 例3

**Figmaデザイン**([link](https://www.figma.com/design/79YtCDYtmvzSclE1f286cA/Stock-UI--Community-?node-id=0-1&p=f&t=aFWcXT6qVHkw349q-0))
![figma-3](/images/kombai-frontend/figma-3.png)

**Kombaiの生成物**:
![example-3](/images/kombai-frontend/example-3.png)

所感は以下のとおり:

- **Pixel Perfect（ピクセル再現）ではない**
- **最初のMockとしては十分**
- **透過系が少し苦手そう**
- **Few-shot Promptで改善可能**

Kombaiの公式からデザインの参考例も紹介されているので、どのようなUIが生成できるか参考になると思います。

https://kombai.com/examples

## まとめ

今回はFigma to CodeのAIツール「Kombai」を紹介しました。

- **VSCodeやCursorのプラグインとして使いやすい**
- **SandboxでUIが確認できるのがとても良い**
- **UIのコンパイル成功率が高めなのが結構えらい**
- **Figma to CodeはPixel Perfectではないが、叩き台としては優秀**

今回はフロントエンド用のAIツールでしたが、今後はドメイン特化のコーディングツールもさらに出てくるのではないかと思います。

興味がある人の参考になれば幸いです。

(余談)

タスクバーに動物アイコンが増えてきた...。

![task-bar](/images/kombai-frontend/task-bar.png)

## 𝕏フォローしてくれると嬉しいです！

[𝕏でも情報発信しているので、フォローしていただけると励みになります！](https://x.com/gaishi_narou)

![](/images/x/x-20250802.png =500x)

## 参考文献

- [Kombai - Official Website](https://kombai.com/)
- [Kombai - Product Hunt](https://www.producthunt.com/products/kombai)
- [Kombai Documentation - Tech Stack Configuration](https://docs.kombai.com/core-features/configure-tech-stack)
- [Kombai Examples](https://kombai.com/examples)
- [Figma Community File - Example 1](https://www.figma.com/community/file/1252561852327562039)
- [Figma Design - Stock Portfolio Dashboard](https://www.figma.com/design/eaY2PdzUqfFrSlkHBd3j0e/Stock-Portfolio-Dashboard--Community-?node-id=0-1&p=f&t=QYKekSD0zUGvLPZK-0)
- [Figma Design - Stock UI](https://www.figma.com/design/79YtCDYtmvzSclE1f286cA/Stock-UI--Community-?node-id=0-1&p=f&t=aFWcXT6qVHkw349q-0)
