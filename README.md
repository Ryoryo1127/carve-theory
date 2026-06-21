# CARVE THEORY

スキー・スノーボード技術解説メディア

## セットアップ

### 1. 依存関係のインストール

```bash
npm install
```

### 2. 開発サーバー起動

```bash
npm run dev
```

http://localhost:3000 でアクセス可能。

### 3. ビルド

```bash
npm run build
npm start
```

---

## ディレクトリ構成

```
carve-theory/
├── content/
│   └── articles/          # MDX記事ファイル
│       └── *.mdx
├── public/                # 静的ファイル
├── src/
│   ├── app/               # App Router
│   │   ├── layout.tsx
│   │   ├── page.tsx       # トップページ
│   │   ├── articles/
│   │   │   ├── page.tsx   # 記事一覧
│   │   │   └── [slug]/
│   │   │       └── page.tsx  # 記事詳細
│   │   ├── categories/
│   │   │   ├── page.tsx
│   │   │   └── [slug]/page.tsx
│   │   ├── players/page.tsx
│   │   ├── search/page.tsx
│   │   ├── robots.ts
│   │   └── sitemap.ts
│   ├── components/
│   │   ├── layout/        # Header, Footer
│   │   ├── home/          # トップページセクション
│   │   ├── article/       # 記事UI
│   │   └── ui/            # 共通UI
│   ├── lib/
│   │   ├── articles.ts    # 記事データ管理
│   │   ├── constants.ts   # 定数・データ
│   │   └── utils.ts       # ユーティリティ
│   ├── types/
│   │   └── index.ts       # 型定義
│   └── styles/
│       └── globals.css
├── tailwind.config.ts
├── next.config.mjs
└── vercel.json
```

---

## 記事の書き方

`content/articles/` にMDXファイルを作成する。

```mdx
---
title: "記事タイトル"
subtitle: "サブタイトル"
excerpt: "記事の要約（検索結果・カードに表示）"
category: "carving"          # カテゴリslug
tags: ["タグ1", "タグ2"]
route: "スキー"              # スキー | 技術選 | アルペン | スノーボード
level: "中級"                # 初級 | 中級 | 上級 | 競技
readTime: 15                 # 読了時間（分）
publishedAt: "2025-01-01"
featured: false
relatedSlugs: ["other-article-slug"]
---

## 見出し2

本文。

### 見出し3

本文。
```

---

## Vercelデプロイ手順

1. GitHubリポジトリにpush
2. Vercel (vercel.com) でプロジェクトをImport
3. Framework Preset: **Next.js**を選択
4. Build Command: `next build`（自動検出）
5. Output Directory: `.next`（自動検出）
6. Deploy

環境変数は現状不要。Supabaseを追加する場合は `.env.local` に設定する。

---

## 今後の拡張

### Supabase連携（記事管理CMS化）
```
NEXT_PUBLIC_SUPABASE_URL=...
NEXT_PUBLIC_SUPABASE_ANON_KEY=...
```

### 追加予定機能
- [ ] コメント機能
- [ ] ブックマーク
- [ ] 閲覧履歴
- [ ] 動画埋め込みコンポーネント
- [ ] 技術比較UI（荷重グラフ等）
- [ ] ドリル動画ページ
- [ ] 雪質別詳細ページ
- [ ] タグページ
- [ ] RSS feed
