# monitor.kikaku-note.com

モニターサイズ・解像度・PPI を確認・計算できるシンプルなツールサイトです。

## 特徴

- ✨ 軽量な静的 HTML（ビルド不要）
- 📱 レスポンシブ対応
- 🔧 モニターサイズ計算機
- 📊 主要サイズ早見表
- 🎮 用途別選び方ガイド
- 📚 用語解説

## ファイル構成

```
.
├── index.html           # メインサイト（CSS・JavaScript 内包）
├── robots.txt           # SEO 設定
├── README.md            # このファイル
└── publish-checklist.md # 公開前チェックリスト
```

## Cloudflare Pages 設定

### 推奨設定

| 項目 | 設定値 |
|-----|--------|
| **Framework preset** | None |
| **Build command** | 空欄（ビルド不要） |
| **Build output directory** | `.` |
| **Production branch** | `main` |
| **Custom domain** | `monitor.kikaku-note.com` |

### セットアップ手順

1. **GitHub リポジトリ作成**
   - https://github.com/new で新規リポジトリを作成
   - リポジトリ名: `kikaku-note-monitor`
   
2. **Cloudflare Pages 設定**
   - https://dash.cloudflare.com にログイン
   - Pages > 新しいプロジェクト > GitHub に接続
   - リポジトリを選択
   - ビルド設定:
     - Framework preset: `None`
     - Build command: 空欄
     - Build output directory: `.`
   - 環境変数: なし（GA4 タグは HTML に固定）

3. **Custom domain 追加**
   - Pages > 設定 > Custom domains
   - `monitor.kikaku-note.com` を追加
   - DNS 設定を確認（CNAME: `kikaku-note-monitor.pages.dev`）

## 公開後に確認する URL

- https://monitor.kikaku-note.com/
- https://monitor.kikaku-note.com/robots.txt
- https://monitor.kikaku-note.com/index.html

## GA4 設定

Google Analytics 4 は `index.html` に以下タグが含まれています：

```javascript
<script async src="https://www.googletagmanager.com/gtag/js?id=G-C3M3YRW4B7"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-C3M3YRW4B7');
</script>
```

測定 ID: `G-C3M3YRW4B7`

## SEO 対応

- `<meta name="description">` - 検索流入対策
- `<link rel="canonical">` - 正規 URL 指定
- OGP タグ対応
- robots.txt で Google に sitemap.xml を通知

## 今後の更新

### sitemap.xml 追加時

以下を `kikaku-note.com` の `sitemap.xml` に追加してください：

```xml
<url>
  <loc>https://monitor.kikaku-note.com/</loc>
  <lastmod>2024-05-26</lastmod>
  <changefreq>monthly</changefreq>
  <priority>0.8</priority>
</url>
```

## トラブルシューティング

### ページが表示されない

1. Cloudflare Pages のデプロイ状態を確認
2. Custom domain の DNS 設定を確認（72 時間待つ場合もあります）
3. ブラウザキャッシュをクリア

### GA4 が計測されない

1. Google Analytics の管理画面で測定 ID を確認
2. ブラウザの JS 実行を確認（コンソールエラーをチェック）
3. データ保持期間を確認（最大 14 ヶ月）

## ライセンス

MIT License - 自由に改変・配布可能
