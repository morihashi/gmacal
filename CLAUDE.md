# Project: gmacal Corporate Site

## 1. Purpose
GMA CAL Inc. が提供するモバイルウォレット関連サービスを紹介する公式コーポレートサイトを、**Astro + Tailwind CSS + Netlify** を用いて構築する。  
目標は以下の通り：
- サービス内容を分かりやすく提示し、ブランド価値を向上させる
- モバイル・デスクトップ双方で高速表示（Lighthouse Performance 95点以上）
- SEO最適化、アクセシビリティ確保、将来の多言語化対応
- GitHub + Netlify による自動デプロイ・プレビュー環境構築

---

## 2. Technology Stack
- **Astro**: 静的サイトジェネレーター
- **Tailwind CSS**: ユーティリティファーストCSSフレームワーク
- **Markdown/MDX**: お知らせやブログ用コンテンツ
- **Netlify**: ホスティング、Deploy Preview、フォーム管理
- **GitHub**: バージョン管理とCI/CDトリガー
- **Node.js 18+**

---

## 3. Directory Structure
/public
/images # 静的画像ファイル
_redirects # Netlifyリダイレクト設定
/src
/components # 再利用可能UI（Header, Footer, Card, Buttonなど）
/layouts # ページレイアウト（BaseLayoutなど）
/pages # 各ページ(index.astro, /services/ など)
/styles # Tailwind設定・グローバルCSS
/content # Markdownコンテンツ（必要に応じて）
CLAUDE.md # 本ファイル
netlify.toml # Netlify設定
tailwind.config.mjs # Tailwind設定
postcss.config.cjs # PostCSS設定

markdown
コピーする
編集する

---

## 4. Pages & Routing
**固定ページ**
- `/` トップページ
- `/about/` 会社概要
- `/contact/` お問い合わせフォーム（Netlify Forms対応）
- `/privacy/` プライバシーポリシー
- `/mobile-wallet/` モバイルウォレット
- `/solution/` ソリューション

**サービスページ**
- `/services/` サービス一覧
- `/services/mobile-id-card/`
- `/services/mobile-point-card/`
- `/services/mobile-coupon/`
- `/services/mobile-stamp-card/`
- `/services/mobile-tickets/`

**リダイレクト**
- `/aboutus` → `/about` (301)
- `/privacy-policy` → `/privacy` (301)

---

## 5. Design Guidelines
- HTMLはセマンティックタグを正しく使用（`<header>`, `<main>`, `<footer>` 等）
- 見出しは階層順守（h1 → h2 → h3）
- Tailwind CSSを使用し、再利用パーツは必ずコンポーネント化
- ブランドカラー：
  - プライマリ: `#0066cc`
  - アクセント: `#00cc88`
  - 背景: `#f8f9fa`
- 余白・フォントはTailwindのspacing/typographyを統一
- アイコンは Heroicons またはSVG直書き

---

## 6. Accessibility (A11y)
- 全画像に `alt` 属性を設定
- フォーカス可能要素には `:focus-visible` スタイル
- スキップリンク実装（例: `<a class="sr-only focus:not-sr-only" href="#main">`）
- コントラスト比は WCAG AA 以上

---

## 7. Performance & SEO
- Lighthouse 各スコア 95点以上を目標
- ページごとに `<title>` と `<meta name="description">` を設定
- OGPタグ（`og:title`, `og:description`, `og:image`）を `<head>` に追加
- 画像は遅延読み込み（`loading="lazy"`）＋適切なサイズ
- CSSとJSは最小限に分割
- 不要な外部スクリプトは読み込まない

---

## 8. Development Workflow
1. 新ページ作成時は `/src/pages/` に `.astro` ファイルを追加
2. レイアウトは必ず `/src/layouts/BaseLayout.astro` を経由
3. コンポーネントは `/src/components/` に作成し再利用
4. グローバルCSSは `/src/styles/global.css` に記述
5. コミットメッセージは [Conventional Commits](https://www.conventionalcommits.org/) に準拠  
   - 例: `feat: add mobile-id-card service page`
6. GitHubにpushするとNetlifyが自動ビルド＆プレビューURL発行

---

## 9. Netlify Settings
- `netlify.toml` にビルド設定（`npm run build` / `dist`）
- `public/_redirects` でリダイレクト管理
- Deploy PreviewをPRごとに自動生成
- HTTPS常時化・www→apexリダイレクト設定

---

## 10. Future Enhancements
- お知らせページ（Markdown→Astro Content）
- 多言語対応（i18n）
- CMS連携（Contentful / Sanity / Netlify CMS）
- サービス事例ページ追加

---

## 11. Claude Code Rules
- この `CLAUDE.md` の構造とガイドラインに従ってコードを生成する
- コンポーネント・ページ追加時は関連するルーティング、リンク、メタ情報を必ず更新
- SEO・A11y・パフォーマンスを損なうコードは避ける