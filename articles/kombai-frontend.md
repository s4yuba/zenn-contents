---
title: "フロントエンドAI開発ツール「Kombai」を使ってみた"
emoji: "🐕"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: [kombai, ai, frontend]
published: false
---

:::message
- この記事でAIは誤字脱字の検出のために使用しています
- Kombaiは早期アクセスユーザーとして使用しました。もともと案件として最初引き受けたものが面白かったため、依頼されていないにも関わらず記事にしていますが、気になる方はお引き返しください。
:::

Oikonです。外資企業でITエンジニアをしています。

今回は

## Kombaiについて

https://kombai.com/

![benchi](/images/kombai-frontend/benchi.png)

## Kombaiを使ってみる

### インストール

![install](/images/kombai-frontend/install.png)
![install-warning](/images/kombai-frontend/install-warning.png)
![signin](/images/kombai-frontend/signin.png)
![signin-success](/images/kombai-frontend/signin-success.png)

### 自然言語でUIを作成

![demo1-0](/images/kombai-frontend/demo1-0.png)

ポケモン図鑑を作りたい。第一世代の151匹まで全て見れるようにする。

![demo1-1](/images/kombai-frontend/demo1-1.png)
![demo1-2](/images/kombai-frontend/demo1-2.png)
![demo1-3](/images/kombai-frontend/demo1-3.png)

- Framework
- API & State Management
- Router
- Components
- Styling
- Icons
- Global Instructions
- Advanced Configurations

Planning Phaseが存在

![demo1-5](/images/kombai-frontend/demo1-5.png)

![demo1-6](/images/kombai-frontend/demo1-6.png)
![demo1-7](/images/kombai-frontend/demo1-7.png)
![demo1-8](/images/kombai-frontend/demo1-8.png)

ポケモンを151種類にして。あとUIの言語は全て日本語で。

![demo1-9](/images/kombai-frontend/demo1-9.png)
![demo1-10](/images/kombai-frontend/demo1-10.png)

![demo1-11](/images/kombai-frontend/demo1-11.png)

```md:sections.md
### Pokémon List View
Main grid/list view displaying all 151 first-generation Pokémon with thumbnails, names, and basic info

### Pokémon Detail View
Detailed view showing individual Pokémon information including stats, types, abilities, and larger image

### Search and Filter
Search bar and filter options to find Pokémon by name, type, or other criteria

### Navigation Header
Application header with title, navigation, and possibly theme toggle
```

```md:features.md
### Pokémon Grid Display
Grid layout showing all 151 Generation I Pokémon with images, names, types, and ID numbers

### Search Functionality
Search bar allowing users to find Pokémon by name with real-time filtering

### Type Filtering
Filter dropdown to show Pokémon by specific types (Fire, Water, Grass, etc.)

### Pokémon Detail View
Detailed modal or page showing individual Pokémon stats, abilities, description, and larger image

### Responsive Design
Mobile-friendly layout that adapts to different screen sizes

### Type Color Coding
Visual color coding for different Pokémon types throughout the interface

### Navigation Controls
Previous/Next navigation in detail view and back to list functionality
```

`Approve Plan & Start Coding`ボタンを押す

### Figma

## まとめ
