---
title: "ObsidianとClaude Codeを使ったドキュメント管理"
emoji: "💫"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [obsidian, claudecode, ai, claude, mcp]
published: true
published_at: 2025-08-15 07:01
---

:::message
この記事は人力で書いてます。
:::

Oikonです。外資系IT企業でエンジニアをしています。

AIエージェントのコンテキストエンジニアリングが最近は注目を集めています。個人的には今後もこの流れはしばらく続くと思っています。

AIエージェントにコンテキストを与える仕組みのために、**知識の源泉としてObsidianを3ヶ月ほど前から試行錯誤しながら使っています**。

最近になって、ようやく自分の中でしっくり来る運用が固まってきたので、その方法を共有します。

この記事では、先日Xにポストした内容をより詳細に説明します。

https://x.com/oikon48/status/1955918989340893275

Obsidianの運用方法は人によって全く違うと思うので、「こんな運用方法もあるのね」くらいに読んでいただければ幸いです。

## 運用の流れ

まず以下が揃っていることを前提とします。

- [Obsidian Desktop](https://obsidian.md/)
- [Obsidian Mobile](https://apps.apple.com/jp/app/obsidian-connected-notes/id1557175442?l=en-US)(Optional)
- [Claude Code](https://docs.anthropic.com/ja/docs/claude-code/overview)

クリックで、それぞれの公式サイトに飛びます。

はじめに、Obsidianの運用の全体像を紹介します。現在の運用手順は以下の通りです。

1. **Obsidian Vaultをデバイス間で共有**
2. **Obsidian Web Clipperで記事を保存**
3. **Obsidianのフォルダ構成はシンプルに**
4. **Clippings/をClaude Codeで整理**
5. **Claude CodeとObsidian MCPサーバーを繋ぐ**
6. **Claude CodeからObsidianを活用する**

それぞれについて詳しく説明します。

### 1. Obsidian Vaultをデバイス間で共有

![iCloud + GitHub](https://pbs.twimg.com/media/GyTSGKva4AICPuq.jpg)

Obsidian Vault（ドキュメント保管庫）をどこに作るかですが、iCloudに作成しています。Appleアカウントでログインしていれば、ドキュメントフォルダを共有できるので、無料でObsidianを活用できます。Obsidianに課金している方は、あまり気にする必要はないかもしれないです。

iCloudフォルダはGitHubリポジトリも兼ねていて、iCloudでログインしていないデバイスでも、リポジトリをCloneしてくれば同じ運用が可能です。例えばMacとWindows間で共有したいケースなどが挙げられます。またGitHubのリポジトリにすればドキュメントの変更履歴も追うことができます。

つまり以下のように併用しています。

- **iCloud: Appleデバイス間のVault共有**
- **GitHub: MacとWindowsなどのデバイス間のVault共有 + 変更履歴の記録**

二重共有なのでクセがありますが、個人的にはこれで上手くいっています。

### 2. Obsidian Web Clipperで記事を保存

Obsidianの拡張機能 **Obsidian Web Clipper** で、技術記事や参考文献として保存したいドキュメントをObsidianに保存します。

ChromeだけでなくiPhoneでも使用できるので、PC・スマホの両方からいつでもObsidianのClippings/ にドキュメントを一旦投げ込みます。

#### ブラウザ版Obsidian Web Clipper

Chromeなどブラウザの拡張機能は、以下のリンクからインストールします

https://chromewebstore.google.com/detail/cnjifjpddelmedmihgijeibhnjfabmlf?utm_source=item-share-cb

インストールすると、Chromeの拡張機能にObsidianのマークが現れます。**Obsidianに追加**のボタンを押すとデフォルトの`Clippings`フォルダに追加されます。

![Web Clipper](https://pbs.twimg.com/media/GyTSnaZasAAHJ89.jpg =500x)

#### モバイル版Obsidian Web Clipper

モバイル版Obsidian Web Clipperも存在します。以下はApple Storeのリンクです↓

https://apps.apple.com/jp/app/obsidian-web-clipper/id6720708363?l=en-US

iPhoneでObsidian Web Clipperを使うには、URL部分左側の拡張機能をクリックします。

![obsidian-iphone1](/images/obsidian-claude-code/obsidian-iphone1.png =400x)

#### Web Clipperが使えないドキュメント

Web Clipperが使えないものは、リンクやスレッドをChatGPTやGrokに与えてObsidian形式のmdファイルを生成してもらい、同じく`Clippings/`に保存します。

またYoutubeの動画などは、NotebookLMに食わせることで同じことが可能です。

### 3. Obsidianのフォルダ構成はシンプルに

Obsidianについて調べると必ずと言って良いほど**Zettelkasten**という手法を目にしますが、自分には合いませんでした。

フォルダ管理を色々試した結果、以下のような構成に落ち着いています。

- `00_inbox/`: 一時的なキャプチャ、メモ
- `01_sources/`: 外部ソース、知識保存場所
- `02_working/`: 作業中のドラフト
- `03_output/`: 自分の記事など
- `Clippings/`: Obsidian Web Clipperの保存場所

実際のフォルダ：
![フォルダ構成](https://pbs.twimg.com/media/GyTT9Vla4AIFE7_.png =300x)

フォルダ構成は人によって最適なものが違うので、使いながら探す必要があります。

### 4. Clippings/をClaude Codeで整理

![整理プロセス](https://pbs.twimg.com/media/GyTVZoya4AQAItR.jpg)

Obsidian Web Clipperで`Clippings/`にドキュメントを放り込んだあとは、`01_sources/`に振り分けて整理します。

手作業だと手間なので、**Claude Codeのカスタムスラッシュコマンド**を使います。

- tag-list.mdの確認
- Obsidianタグ付け
- フォルダ振り分け
- tag-list.mdの更新

これらを一気に実行するカスタムSlash Commandを作成します。サーバーを立てられる方なら**Clippings/**を監視して、追加されたら即座にタグ付けと振り分けを実行しても良いと思います。

またタグ専用ドキュメント`tag-list.md`で既存タグを管理すると、無尽蔵にObsidianのタグが増えすぎることをある程度防げます。

:::details 実際のカスタムスラッシュコマンド

```md:organize-clippings.md
# クリッピング整理・タグ標準化

Clippingsディレクトリのファイルをコンテンツに基づいて01_sourcesの適切なサブディレクトリに振り分け、タグを標準化します。

**オプション実行モード:**

- `--tags-only`: ファイル移動せず、タグ標準化のみ実行
- `--move-only`: タグはそのまま、ファイル移動のみ実行
- デフォルト: 移動とタグ標準化を両方実行

以下の手順で実行してください：

&#35;&#35; Step 1: Clippingsディレクトリの内容を確認

Clippingsディレクトリ内のすべてのMarkdownファイルをリストアップし、各ファイルの内容とタグを確認します。

&#35;&#35; Step 2: ファイルのカテゴリ分析

各ファイルの内容、タイトル、タグを分析して、以下のカテゴリに分類します：

&#35;&#35;&#35; 既存の01_sourcesサブディレクトリ：

- **ai_engineering/**: AIエンジニアリング、Agentic Software Engineering、コンテキストエンジニアリング関連
- **ai_tools/**: Claude Code、Kiro、Gemini CLI、Cursor、Windsurf等のAIコーディングツール
- **ai_tools_kiro_250724/**: Kiro専用ドキュメント（既に多数存在）
- **business/**: ビジネスモデル、マーケティング、収益化、スタートアップ関連
- **clips/**: 短い記事クリップ、ブログ記事、一般的なウェブクリップ
- **references/**: 技術リファレンス、プログラミング言語、開発手法、ガイド類
- **tool_obsidian/**: Obsidian関連のツールやワークフロー

上記に該当しない場合、新規でFolderを作成する。名前は適宜つけること

&#35;&#35; Step 3: ファイルの移動

各ファイルを適切なディレクトリに移動します：

&#96;&#96;&#96;&#96;bash
# 基本的な移動コマンド例
mv "Clippings/[ファイル名].md" "01_sources/[適切なカテゴリ]/[ファイル名].md"
&#96;&#96;&#96;&#96;

&#35;&#35; 分類ガイドライン：

1. **Kiro関連** → `ai_tools/` または `ai_tools_kiro_250724/`（内容の詳細度による）
2. **Claude Code、Gemini CLI等** → `ai_tools/`
3. **AIエージェント、開発手法論** → `ai_engineering/`
4. **ビジネス戦略、起業** → `business/`
5. **技術チュートリアル、MCP** → `references/`
6. **Webサービス開発** → `web_development/`（新規作成）
7. **プロダクト事例、失敗談** → `product_development/`（新規作成）
8. **一般的なクリップ** → `clips/`

&#35;&#35; Step 4: 必要に応じて新規ディレクトリ作成

01_sources直下に新しいカテゴリが必要な場合は作成します：

&#96;&#96;&#96;&#96;bash
mkdir -p "01_sources/web_development"
mkdir -p "01_sources/product_development"
&#96;&#96;&#96;&#96;

&#35;&#35; Step 5: タグの標準化

各ファイル（移動した場合は移動先、`--tags-only`の場合はClippings内）について、`.claude/tag-list.md`に基づいてタグを標準化します：

**タグ標準化の詳細手順：**

1. **標準タグリストの参照**
   - `.claude/tag-list.md`から利用可能な標準タグを確認

2. **既存タグの分析**
   - 現在のタグを確認
   - `clippings`タグは削除対象としてマーク

3. **標準タグへのマッピング**
   - 既存タグを標準タグにマッピング
   - アンダースコア → ハイフン変換（claude_code → claude-code）
   - 日本語タグは標準リストの対応するものを使用

4. **新規タグの追加**
   - コンテンツ内容に基づいて適切な標準タグを4-6個程度追加
   - 以下のカテゴリから選択：
     - **AI・開発**: ai-tools, claude-code, kiro, ai-development, ai-agents
     - **技術**: React, TypeScript, engineering, software-development, frontend
     - **ビジネス**: startup, monetization, marketing, indie-dev, entrepreneurship
     - **コンテンツタイプ**: tutorial, case-study, japanese, review, documentation

5. **タグの更新・整理**
   - フロントマターのtagsセクションを更新
   - 重複を除去し、アルファベット順にソート
   - 既存の有用な情報は保持

**重要なマッピング例：**

- `"claude-code"` → claude-code
- `"kiro"` → kiro  
- `"AI"` → ai-development, ai-tools, ai-agents（文脈依存）
- `"security"` → security, ai-security
- `"開発効率化"` → 開発効率化（日本語版を標準リストから使用）
- `"IDE"` → 具体的なツール名に置換または削除

&#35;&#35; Step 6: 整理結果の確認

移動後、以下を確認します：

- Clippingsディレクトリが空になっていること
- 各ファイルが適切なカテゴリに配置されていること
- 全ファイルのタグが標準化されていること

&#35;&#35; Step 7: 完了報告

移動したファイル数、各カテゴリへの振り分け結果、タグ標準化の結果をレポートします。

---

**注意事項：**

- ディレクトリ階層は01_sources直下の1階層のみ（最大深度：01_sources/category/）
- ファイル名にスペースや特殊文字が含まれる場合は適切にクォート
- 移動前にバックアップを推奨
- 既存の有用な情報は保持し、タグのみ標準化すること
- `.claude/tag-list.md`にない重要なタグが見つかった場合は、tag-listに追加を検討すること

```

:::

### 5. Claude CodeとObsidian MCPサーバーを繋ぐ

![活用方法](https://pbs.twimg.com/media/GyTXmrOa4AQywvc.jpg)

Obsidianに蓄えたドキュメントは、基本的にはMCPサーバー経由で活用しています。

Obsidian MCPサーバーはいくつか存在しますが、Obsidian Desktopからローカル接続するのが個人的には良かったです。MCPサーバーのツール群が一番使い易いことが理由です。

まずObsidian Desktopでコミュニティプラグインを2つ入れます

- **Local REST API**
- **MCP Tools**

この2つのプラグインにより、ローカルAPI（APIキー）とMCPサーバー機能を利用できます。

Claude CodeでこのObsidian DesktopのMCPサーバーに繋ぐには以下のコマンドを実行します。

```bash
  # "/path/to/vault" はご自身の環境に合わせて修正してください
  claude mcp add obsidian-mcp-tools -s user -- "/path/to/vault/.obsidian/plugins/mcp-tools/bin/mcp-server" --env OBSIDIAN_API_KEY=YOUR_API_KEY
```

もしくは`.claude.json`に自分で追加します。

```json
  {
    "mcpServers": {
      "obsidian-mcp-tools": {
        "command": "/path/to/vault/.obsidian/plugins/mcp-tools/bin/mcp-server",
        "args": [],
        "env": {
          "OBSIDIAN_API_KEY": "YOUR_API_KEY"
        }
      }
    }
  }
```

既にClaude DesktopとObsidianをMCPサーバーで連携している人は、以下のコマンドでClaude Codeでも設定できます。

```bash
claude mcp add-from-claude-desktop
```

Claude CodeとObsidian MCPサーバーが上手く接続できているかは、以下のコマンドで確認できます。

**Terminal**:

```bash
claude mcp list
```

`obsidian-mcp-tools: /path/to/.obsidian/plugins/mcp-tools/bin/mcp-server`が表示されているはずです

**Claude CodeのSlash Command**:

```bash
/mcp
```

`obsidian-mcp-tools  ✔ connected · Enter to view details`が表示されているはずです。

### 6. Claude CodeからObsidianを活用する

実際にObsidianに蓄えたドキュメントを活用します。Obsidianのドキュメントの活用方法は人によって千差万別ですが、私の場合は以下のように活用しています。

主な活用方法：

- **タグからドキュメント検索**
- **技術記事の内容の査読**
- **参考文献用のリンクの取得**
- **登壇スライド内のコンテンツ作成**

これらをObsidianのドキュメントを使って、AIエージェントのコンテキストとして与えます。ドキュメントをVSCode上から扱えるようにしていて、Obsidian Desktopはサーバー的な役割で起動するのみです。

一応ObsidianのコミュニティプラグインのTerminalを使ってClaude Codeを実行できるのですが、個人的にはVSCode（もしくはCursor）でObsidianのフォルダを弄る、もしくはMCPサーバー経由で活用する方がよかったです。

### Obsidian運用の流れまとめ

ここまでの流れをまとめると、以下の運用になります。

1. **Obsidian Vaultをデバイス間で共有**
2. **Obsidian Web Clipperで記事を保存**
3. **Obsidianのフォルダ構成はシンプルに**
4. **Clippings/をClaude Codeで整理**
5. **Claude CodeとObsidian MCPサーバーを繋ぐ**
6. **Claude CodeからObsidianを活用する**

## まとめ

Obsidianが便利だと感じるまでに3ヶ月ほどかかりました。

Obsidian活用の個人的なコツは以下の通りです:

- 雑に放り込む
- AIに編集を任せる
- AIに整理を任せる
- AIに解説を任せる
- AIに引用を任せる
- 人間は文献付きの成果物だけを扱う

Obsidianは自由度が高い故に挫折してしまうことが多いですが、**AI-Firstを心掛けると上手く活用できるのではないか**と考えています。

今後は自分の考えや知識のドキュメントが資産になって、生成AIに活用させる機会がますます増えているため、Obsidianに限らずドキュメント管理は重要になると思っています。

この記事が参考になれば幸いです。

## 𝕏フォローしてくれると嬉しいです！

[𝕏でも情報発信しているので、フォローしていただけると励みになります！](https://x.com/oikon48)

![](/images/x/x-20250815.png =500x)

## 参考文献

### 公式ドキュメント・ツール

https://obsidian.md/

https://docs.anthropic.com/ja/docs/claude-code/overview

https://chromewebstore.google.com/detail/cnjifjpddelmedmihgijeibhnjfabmlf?utm_source=item-share-cb

https://apps.apple.com/jp/app/obsidian-connected-notes/id1557175442?l=en-US

https://note.com/chankostin/n/n41004bfbda6e

https://note.com/electrical_cat/n/n5db5f038a391
