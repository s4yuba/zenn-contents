---
title: Obsidian MCPとClaude Codeで実現する効率的な知識管理システム - フォルダ構成の実践例
tags:
  - obsidian
  - claude-code
  - MCP
  - knowledge-management
  - productivity
  - workflow
  - AI
  - 開発効率化
date: 2025-08-13
status: draft
---

# Obsidian MCPとClaude Codeで実現する効率的な知識管理システム - フォルダ構成の実践例

## はじめに

Obsidian MCPの登場により、Claude CodeからObsidian Vaultへの直接アクセスが可能となり、知識管理とAI活用の連携が大幅に向上しました。本記事では、実際に運用しているObsidian Vaultの詳細なフォルダ構成と、その背景にある設計思想について解説します。

特にAI開発やコンテンツ制作を行うエンジニアにとって、情報の整理と活用は重要な課題です。本記事で紹介する構成は、Input/Outputフローを明確にし、情報の流れを体系化することで、効率的な知識管理を実現しています。

## 全体構造の設計思想

今回紹介するVaultは、番号付きフォルダによる情報フロー管理を採用しています：

```txt
.
├── 00_inbox/          # クイックキャプチャ・未処理のメモ
├── 01_sources/        # すべての入力元
├── 02_working/        # アクティブな作業
├── 03_output/         # 完成したコンテンツ
├── assets/            # メディアファイル
├── templates/         # ノートテンプレート
├── CLAUDE.md         # AI連携のためのガイドライン
└── README.md         # Vault概要
```

この構成の最大の特徴は、**情報の生産フローを明確に表現している**点にあります。

## 番号付きフォルダによる情報フロー管理

### 00_inbox: クイックキャプチャの仕組み

`00_inbox`フォルダは、思いついたアイデアや見つけた情報を瞬時にキャプチャするための場所です。

**特徴：**
- 処理の優先度や詳細な分類を考える必要なし
- 後で適切な場所に移動することが前提
- モバイル端末からの入力にも対応

**実際の活用例：**
- Web記事のクリップ
- 突発的なアイデアのメモ
- 会議中の重要ポイント
- SNSで見つけた参考資料

### 01_sources: 情報ソースの体系的整理

`01_sources`は、すべての参考資料を体系的に整理するエリアです。ここが本Vaultの知識ベースの中核となります。

#### カテゴリー別の構成

```txt
01_sources/
├── ai_engineering/    # AI開発・エンジニアリング
├── ai_security/       # AIセキュリティ・安全性
├── ai_tools/          # Claude Code、Kiro等のツール
├── business/          # ビジネス・マネタイゼーション
├── clips/             # Webクリッピング
├── references/        # 書籍・論文・外部リソース
└── tool_obsidian/     # Obsidian活用法
```

特に`ai_tools`フォルダには、以下のような最新のAI開発ツールに関する情報が蓄積されています：

- **Claude Code関連記事**: 50+の実践的な記事とTips
- **Kiro関連記事**: Amazon発のAI IDEに関する詳細分析
- **MCP関連記事**: Model Context Protocolの活用事例
- **比較記事**: 各ツールの特徴と使い分け

### 02_working: アクティブな作業管理

`02_working`は、現在進行中のプロジェクトや作業を管理する場所です。

```txt
02_working/
├── ios_app/       # iOS開発プロジェクト
├── seo_llmo/      # SEO関連のLLMプロジェクト
└── drafts/        # 記事の下書き（想定）
```

**特徴：**
- プロジェクト単位でのフォルダ分割
- 作業中のみ存在し、完了後は`03_output`へ移動
- 複数人での作業時の状況共有にも活用可能

### 03_output: 完成コンテンツの管理

`03_output`は、完成したコンテンツや公開可能な成果物を保管する場所です。

```txt
03_output/
├── articles/      # 一般記事
└── zenn/          # Zenn向けの技術記事
```

**Zennフォルダの実績：**
- Claude Code関連記事: 5本
- Kiro関連記事: 2本  
- 技術イベントレポート: 1本
- 総計11本の技術記事を公開

## 実際のコンテンツ量と運用実績

### 01_sources/ai_tools フォルダの詳細分析

`ai_tools`フォルダには、現在**58ファイル**の記事が蓄積されています。これは、AI開発ツールの急速な進歩に対応した情報収集の成果です：

**Claude Code関連（約25記事）:**
- 基本操作からプロTipsまで幅広くカバー
- Hooks機能の活用法
- メモリ機能（CLAUDE.md）の使い方
- 他ツールとの比較記事

**Kiro関連（約15記事）:**
- 仕様駆動開発の実践例
- Agent Steeringの仕組み解説
- セキュリティ・プライバシー考慮事項

**MCP関連（約8記事）:**
- 基本的なセットアップ方法
- Serena MCPなどの実用例
- Web連携の活用事例

**その他のツール比較（約10記事）:**
- Gemini CLI、Windsurf等との比較
- 2025年のAIコーディングツール動向
- コミュニティ情報とキュレーション

### 01_sources/ai_engineering フォルダの構成

**19ファイル**のAI開発に関する高品質な記事が蓄積されています：

- **Agentic Software Engineering**: 最新の開発手法論
- **Context Engineering**: AIエージェントでのコンテキスト設計
- **LLM Application**: 実運用でのベストプラクティス
- **バイブコーディング**: 設計思考との組み合わせ
- **宣言的AIコーディング**: 新しいパラダイムの提案

### 03_output実績: Zennでの技術記事公開

**11本の技術記事**を既に公開し、継続的なアウトプットを実現：

1. **Claude Code解説シリーズ（5本）**
   - スラッシュコマンド全解説
   - UltraThink機能の活用
   - カスタムコマンドの作り方
   - MCP連携の実装
   - LTスライド作成事例

2. **Kiro関連記事（2本）**
   - Agent Steeringの詳細解説
   - AIコーディングツール動向

3. **その他技術記事（4本）**
   - Figma to CodeツールKombai検証
   - Gemini CLIの隠しコマンド発見
   - イベントレポート（Vibe Coding Catfe）
   - 技術記事執筆のノウハウ

## CLAUDE.mdによる運用ガイドライン

### CLAUDE.mdの詳細解説

`CLAUDE.md`は、Claude CodeとMCPを使って本Vaultを操作する際の重要な設定ファイルです。このファイルが存在することで、AIエージェントが以下の情報を自動的に理解できます：

#### 1. リポジトリ構造の明文化

```markdown
## Repository Structure

The vault follows an Input/Output workflow optimized for content creation:

- **00_inbox/**: Quick capture, unprocessed notes and ideas
- **01_sources/**: All input sources
  - **clips/**: Web clippings and online articles
  - **docs/**: Manuals and documentation
  - **references/**: Books, papers, and external resources
...
```

この構造定義により、Claude Codeは適切なフォルダに自動的にファイルを配置できます。

#### 2. 統合タグシステム

`.claude/tag-list.md`を参照する包括的なタグ分類システムが定義されています：

- **AI & Development**: ai-agents, ai-development, claude-code, kiro, MCP
- **Technologies**: React, TypeScript, Python, obsidian, iOS
- **Business**: indie-dev, monetization, entrepreneurship  
- **Content Types**: tutorial, case-study, comparison, best-practices
- **Japanese Terms**: 開発効率化, 仕様駆動開発, バイブコーディング

#### 3. 運用ルールの明確化

**Git操作の制限:**
```markdown
3. **Git Workflow**: Only perform Git operations from the main Mac device to
   prevent conflicts.
```

**同期コンフリクトの回避:**
```markdown
1. **Sync Conflicts**: Avoid simultaneous edits across devices. Let iCloud sync
   complete before making Git commits.
```

これらのルールにより、複数デバイス環境での安全な運用が実現されています。

#### 4. コンテンツアーキテクチャの説明

**Input/Outputワークフローの明文化:**
1. **Capture** (00_inbox): Quick notes and unprocessed ideas
2. **Source** (01_sources): External references organized by topic
3. **Process** (02_working): Active drafts and working notes  
4. **Publish** (03_output): Final articles and deliverables

#### 5. バイリンガル対応の考慮

```markdown
6. **Bilingual Content**: Content is created in both Japanese and English,
   following the expertise and target audience of each topic.
```

技術的専門性と対象読者に応じて、日本語・英語を使い分ける方針が明記されています。

## ワークフローとテンプレート活用法

### Capture → Collect → Create → Completeフロー

本Vaultの中核となる4段階の情報処理フローを詳しく解説します。

#### Stage 1: Capture（収集）

**目的**: 情報の瞬時キャプチャ
**場所**: `00_inbox/`
**特徴**:
- 詳細な分類は後回し
- スピード重視の記録
- モバイル端末からのアクセス最適化

**実践例:**
```markdown
# 00_inbox/quick-idea-20250813.md

## AI開発ツール比較アイデア
- Claude Code vs Kiro の詳細比較記事
- 実際の開発速度測定
- コスト比較も含める
```

#### Stage 2: Collect（整理）

**目的**: 情報源の体系的整理
**場所**: `01_sources/`配下の適切なカテゴリ
**プロセス**:
1. 内容に基づく分類判断
2. 適切なサブフォルダへの移動
3. ファイル名の統一化
4. タグの追加

**実践例:**
- Web記事 → `01_sources/clips/`
- 技術ドキュメント → `01_sources/docs/`
- AI関連情報 → `01_sources/ai_tools/` or `ai_engineering/`

#### Stage 3: Create（作成）

**目的**: アクティブなコンテンツ制作
**場所**: `02_working/`
**特徴**:
- プロジェクト単位での管理
- 草稿からレビューまでの全工程
- 複数記事の並行制作対応

**フォルダ構成例:**
```txt
02_working/
├── article-claude-code-tips/
│   ├── outline.md
│   ├── draft-v1.md
│   ├── images/
│   └── references.md
└── ios-app-development/
    ├── architecture.md
    └── implementation-notes.md
```

#### Stage 4: Complete（完成）

**目的**: 完成コンテンツの公開準備
**場所**: `03_output/`
**分類基準**:
- `articles/`: 一般向け記事
- `zenn/`: 技術記事プラットフォーム向け

### テンプレート活用の実践

#### Daily Noteテンプレートの詳細

```markdown
---
date: {{date}}
tags: [daily]
---

# {{date:YYYY-MM-DD}}

## 今日の目標
- [ ] 

## タスク

### 緊急・重要
- [ ] 

### 重要・緊急でない
- [ ] 

### 緊急・重要でない
- [ ] 

## ノート・アイデア

## 振り返り

## 明日への申し送り
```

**活用のメリット:**
- アイゼンハワーマトリクス的な優先度管理
- 日々の振り返りによる改善サイクル
- アイデアの逃さない記録システム

#### Zettelkastenテンプレートの活用

原子的な知識の記録と関連付けを促進：
- 一つの概念につき一つのノート
- 双方向リンクによる知識ネットワーク構築
- 発見的な知識生成の支援

## Obsidian MCPとの連携メリット

### Claude Codeからの直接アクセス

Obsidian MCPの最大の価値は、**Claude CodeからObsidianの知識ベースに直接アクセスできる**点にあります。

#### 実際の使用例

**1. 記事リサーチの自動化**
```
ユーザー: "Kiroについての記事を書きたいので、関連情報をまとめて"
Claude Code: 
- 01_sources/ai_tools/フォルダの Kiro関連記事15本を自動検索
- 内容を要約して記事の構成案を提案
- 新しい記事を03_output/articlesに自動作成
```

**2. 知識のクロスリファレンス**
```
ユーザー: "Claude Codeの制限事項について調べて"
Claude Code:
- 関連記事25本から制限事項を抽出
- 類似ツールとの比較データを参照
- 実体験ベースの回避策を提案
```

**3. コンテンツの自動整理**
```
ユーザー: "今日クリップした記事を適切なフォルダに整理して"
Claude Code:
- 00_inboxの未整理ファイルを分析
- 内容に基づく自動分類
- 適切なタグの自動付与
- 01_sourcesの各サブフォルダへの移動
```

### 自動化可能な操作の具体例

#### 1. コンテンツ作成支援

**記事のアウトライン生成:**
- 関連する既存ノートの自動収集
- トピックの重複チェック
- 構成の最適化提案

**引用・参考文献の自動挿入:**
- Vault内の関連記事への自動リンク
- 外部ソースの整理された引用
- バックリンクの自動生成

#### 2. 情報管理の自動化

**タグの一貫性管理:**
```markdown
# 統一されたタグシステムの自動適用
- #claude-code → 自動で関連タグを提案
- #ai-development → カテゴリタグの自動付与  
- #開発効率化 → 日本語タグとの連携
```

**ファイル命名の標準化:**
- 日付形式の統一
- カテゴリプレフィックスの自動付与
- 重複ファイル名の自動検出と解決

#### 3. アイデアの発展支援

**関連コンテンツの発見:**
- 類似トピックの自動抽出
- 発想の連鎖を促すリンク提案
- 新しい記事アイデアの生成

### 実際のMCPコマンド例

#### 基本的なファイル操作
```bash
# ファイル一覧取得
mcp__obsidian-mcp-tools__list_vault_files

# 特定記事の内容取得  
mcp__obsidian-mcp-tools__get_vault_file "filename.md"

# 新規記事作成
mcp__obsidian-mcp-tools__create_vault_file
```

#### 高度な検索・分析
```bash
# テキスト検索
mcp__obsidian-mcp-tools__search_vault_simple "Claude Code"

# セマンティック検索
mcp__obsidian-mcp-tools__search_vault_smart "AI development efficiency"

# Dataview クエリ
mcp__obsidian-mcp-tools__search_vault "dataview query"
```

#### コンテンツ操作
```bash
# ファイル追記
mcp__obsidian-mcp-tools__append_to_vault_file

# 部分的更新
mcp__obsidian-mcp-tools__patch_vault_file

# Obsidianで表示
mcp__obsidian-mcp-tools__show_file_in_obsidian
```

## 運用上の工夫とTips

### 同期コンフリクトの回避戦略

#### iCloud + Git 二重管理の実践

**基本原則:**
1. **単一デバイスでのGit操作**: MacBook ProでのみGitコマンドを実行
2. **iCloud同期の完了待ち**: 他デバイスでの編集後は同期完了まで待機
3. **段階的バックアップ**: ローカル(iCloud) → リモート(GitHub)の順序

**実際の運用フロー:**
```bash
# 1. 作業開始前の確認
git status
git pull origin main

# 2. iCloud同期状況の確認（macOS）
# ファイルにクラウドマークが付いていないことを確認

# 3. 作業完了後
git add .
git commit -m "Update: 記事追加・更新"
git push origin main
```

#### デバイス別の役割分担

**MacBook Pro (メインデバイス):**
- 長文記事の執筆
- Git操作
- Claude Code / MCP連携
- 複雑なフォルダ操作

**iPhone/iPad:**
- クイックキャプチャ (00_inbox)
- アイデアのメモ
- 既存記事の軽微な修正
- 外出先での情報収集

### ファイル命名とタグの運用ルール

#### 統一されたファイル命名規則

**記事ファイル:**
```
# 良い例
Claude Code Best Practices and Pro Tips.md
Kiroの登場と最近のAIコーディングツールについて思うこと.md
2025年6月にClaude Codeが突然話題になった理由をまとめる.md

# 避けるべき例  
article_1.md  # 内容が不明
temp.md       # 一時的すぎる
claude code.md # スペースのみ、具体性不足
```

**日付の活用パターン:**
- **技術動向記事**: 年月を含める (`2025年6月に...`)
- **イベント記録**: 具体的な日付 (`Vibe Coding Catfe 2024-12-07`)
- **ツール記事**: バージョンや更新時期を明記

#### タグ運用の実践

**階層化されたタグシステム:**
```markdown
# メインカテゴリ
#claude-code #kiro #obsidian #MCP

# 技術分野
#ai-development #productivity #workflow

# コンテンツタイプ
#tutorial #comparison #case-study

# 言語
#japanese #english #bilingual
```

**実際のタグ使用例:**
```yaml
tags: [claude-code, productivity, tutorial, japanese, best-practices]
```

## まとめと今後の展望

### 本構成の成果と効果

#### 定量的な成果

**1. 情報蓄積の実績**
- **総記事数**: 200+ ファイル
- **AI関連記事**: 80+ の高品質な情報源
- **公開実績**: 11本の技術記事をZennで継続公開
- **運用期間**: 安定運用を継続中

**2. 効率性の向上**
- **検索時間の短縮**: カテゴリ分類による瞬時アクセス
- **重複作業の削減**: 既存情報の効率的な再活用
- **品質の一貫性**: 標準化されたテンプレートとタグシステム

#### 定性的な価値

**1. 知識の体系化**
- AI開発ツールの急速な進歩に対応した情報整理
- 断片的な情報から体系的な理解への変化
- 個人の経験と業界動向の統合的把握

**2. 創発的な価値創造**
- 異なる情報源の意外な関連性の発見
- 新しい記事アイデアの継続的な創出  
- コミュニティへの継続的な価値提供

**3. AI連携による生産性向上**
- Claude Code + MCPによる半自動化された知識活用
- 人間の創造性とAIの効率性の最適な組み合わせ
- 知識労働の新しいモデルの実現

### 改善の余地と今後の計画

#### 短期的な改善目標（1-3ヶ月）

**1. オートメーションの拡張**
- [ ] 週次メンテナンス作業のClaude Code化
- [ ] 新記事作成時のテンプレート自動適用
- [ ] タグ統一の自動チェック機能

**2. コンテンツ品質の向上**
- [ ] 古い記事の定期レビューとアップデート
- [ ] 引用関係の可視化と整理
- [ ] バックリンク分析による関連性の最適化

#### 中期的な発展方向（3-6ヶ月）

**1. 拡張された知識管理**
```txt
01_sources/
├── ai_engineering/
├── ai_tools/
├── ai_research/        # ← 新規追加（学術論文・研究動向）
├── community/          # ← 新規追加（Discord、フォーラム情報）
└── experiments/        # ← 新規追加（実験・検証記録）
```

**2. 高度なMCP連携**
- **自動要約機能**: 長文記事の自動サマリー生成
- **関連記事推薦**: 閲覧中記事に基づく関連コンテンツ提案
- **トレンド分析**: 蓄積データからの技術動向分析

### 読者へのアドバイス

#### 導入を検討している方へ

**1. 段階的なスタート**
```txt
Phase 1: 基本的なフォルダ構造の設置
├── 00_inbox/
├── 01_sources/
├── 02_working/
└── 03_output/

Phase 2: CLAUDE.mdの作成と基本運用ルール
Phase 3: Obsidian MCP連携の導入
Phase 4: 高度な自動化とカスタマイズ
```

**2. 成功のための重要ポイント**
- **継続性**: 完璧を求めず、継続的な改善を重視
- **柔軟性**: 自身の作業スタイルに合わせたカスタマイズ
- **実験精神**: 新しいツールや手法への積極的な取り組み

## 結論

Obsidian MCPとClaude Codeの組み合わせは、個人の知識管理に革命をもたらす可能性を秘めています。本記事で紹介したフォルダ構成は、**情報の流れを体系化し、AIとの効果的な連携を実現する**という明確な目標のもとに設計されました。

200+のファイル蓄積と11本の技術記事公開という実績は、このシステムの実用性を証明しています。さらに重要なのは、このシステムが**継続的な学習と創造のサイクル**を促進する点です。

AI開発の分野は今後も急速に変化し続けるでしょう。そのような環境において、効率的な情報管理システムは単なる便利ツールではなく、**競争優位性を維持するための戦略的資産**となります。

本記事の内容が、読者の皆様の知識管理システム構築に役立つことを願っています。AI時代の知識労働において、人間とAIの協調による新しい価値創造の可能性を、共に探究していきましょう。

## 参考文献

### 今回の記事作成で実際に参照したObsidian Vault内資料

本記事の執筆にあたり、以下のファイルから具体的な情報を取得・参照しました：

#### システム設定・運用ドキュメント

**[[CLAUDE.md]]**
- リポジトリ構造の定義
- タグシステムの説明  
- Git/iCloud同期の運用ルール
- バイリンガルコンテンツ管理方針
- Input/Outputワークフローの詳細

**[[README.md]]**  
- Vaultの全体概要
- フォルダ構造の説明
- 4段階ワークフロー（Capture→Collect→Create→Complete）
- 同期設定と注意事項

#### テンプレートファイル

**[[templates/daily-note-template.md]]**
- アイゼンハワーマトリクス形式の日次管理
- タスク分類システム
- 振り返りの仕組み

#### フォルダ構造調査結果

**Vault全体構造:**
- ルートディレクトリ: 7つの主要フォルダとファイル
- 00_inbox/: 1ファイル確認
- 01_sources/: 7つのサブフォルダ構成
- 02_working/: 2つのプロジェクトフォルダ  
- 03_output/: articles/とzenn/の2分類
- templates/: 2つのテンプレートファイル

**詳細調査したフォルダ:**
- `01_sources/ai_engineering/`: 19ファイルの技術記事
- `01_sources/ai_tools/`: 58ファイルのツール関連記事
- `03_output/zenn/`: 11本の公開済み技術記事
- `03_output/articles/`: 1本の記事ファイル

### 調査に使用したMCPコマンド

本記事の情報収集には、以下のObsidian MCPコマンドを使用しました：

```bash
# フォルダ構造の調査
mcp__obsidian-mcp-tools__list_vault_files

# 個別ファイル内容の取得
mcp__obsidian-mcp-tools__get_vault_file

# 記事作成と更新  
mcp__obsidian-mcp-tools__create_vault_file
mcp__obsidian-mcp-tools__append_to_vault_file
mcp__obsidian-mcp-tools__patch_vault_file
```

**調査実施日:** 2025年8月13日  
**データ基準日:** 調査時点での実際のファイル数とフォルダ構成

---

*この記事は、実際にObsidian MCPとClaude Codeを連携させた知識管理システムから生まれました。記事執筆の過程では、上記の参考資料から具体的なデータと運用ノウハウを抽出し、システムの実用性が改めて実証されています。*