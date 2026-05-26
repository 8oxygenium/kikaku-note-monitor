# 公開前チェックリスト

monitor.kikaku-note.com を公開する前に、以下のチェックリストを実行してください。

---

## 📋 チェックリスト

### 初期設定

- [ ] **GitHub リポジトリ作成**
  - リポジトリ名: `kikaku-note-monitor`
  - 説明: `Monitor size reference and calculator for kikaku-note.com`
  - Visibility: Public
  - Add README.md: チェック済み（このプロジェクトで作成）
  - .gitignore: Python（デフォルト可）

- [ ] **コード Push**
  ```bash
  git init
  git add .
  git commit -m "Initial commit: monitor site"
  git branch -M main
  git remote add origin https://github.com/<USERNAME>/kikaku-note-monitor.git
  git push -u origin main
  ```

### Cloudflare Pages 設定

- [ ] **Cloudflare Pages プロジェクト作成**
  - https://dash.cloudflare.com/pages へアクセス
  - 「新しいプロジェクト」をクリック
  - GitHub に接続
  - リポジトリ選択: `kikaku-note-monitor`
  
- [ ] **ビルド設定確認**
  - Framework preset: `None`
  - Build command: 空欄（ビルド不要）
  - Build output directory: `.`
  - Production branch: `main`
  - ✅ 保存してデプロイ開始

- [ ] **Cloudflare Pages でのデプロイ完了待機**
  - https://dash.cloudflare.com/pages でデプロイ状態確認
  - デプロイ成功時に自動 URL が割り当てられます
  - 例: `https://kikaku-note-monitor.pages.dev`

### Custom Domain 設定

- [ ] **Custom domain 追加**
  - Pages > 設定 > Custom domains
  - 「Custom domain を設定」をクリック
  - ドメイン入力: `monitor.kikaku-note.com`
  - ✅ 追加

- [ ] **DNS 設定確認**
  - Cloudflare の DNS 設定で CNAME レコード確認
  - Name: `monitor`
  - Type: `CNAME`
  - Content: `kikaku-note-monitor.pages.dev`
  - ✅ DNS 伝播待ち（通常 5 分～24 時間）

- [ ] **HTTPS 自動化**
  - Cloudflare で自動 SSL/TLS 証明書取得（自動）
  - 「Edge Certificates」で「Universal SSL/TLS」確認

### サイト動作確認

- [ ] **ページ表示確認**
  - https://monitor.kikaku-note.com/ にアクセス
  - ✅ HTML が正常に表示される
  - ✅ レスポンシブ対応（スマホで確認）

- [ ] **機能テスト**
  - [ ] モニター計算機動作確認
    - インチ、アスペクト比、解像度を入力
    - 計算ボタン実行
    - ✅ 横幅・高さ・PPI が表示される
  
  - [ ] タブ切り替え動作確認
    - FHD / WQHD / 4K / 5K / UW タブクリック
    - ✅ 各タブの早見表が表示される
  
  - [ ] 関連リンク確認
    - kikaku-note.com へのリンク確認
    - ✅ 正常にリンク

- [ ] **robots.txt 確認**
  - https://monitor.kikaku-note.com/robots.txt にアクセス
  - ✅ 内容が表示される

- [ ] **OGP タグ確認**
  - 開発者ツール > ネットワーク で HTML ソース確認
  - ✅ og:title, og:description, og:url が含まれている

- [ ] **GA4 タグ確認**
  - 開発者ツール > Console で GA タグが読み込まれているか確認
  - ✅ エラーなし

### SEO・インデックス設定

- [ ] **kikaku-note.com トップページ更新**
  - kikaku-note の トップページに monitor サイトへのリンク追加
  - 例：「関連ツール」セクションに追加
  - ✅ 更新完了

- [ ] **kikaku-note.com sitemap.xml 更新**
  - `sitemap.xml` に以下を追加：
    ```xml
    <url>
      <loc>https://monitor.kikaku-note.com/</loc>
      <lastmod>2024-05-26</lastmod>
      <changefreq>monthly</changefreq>
      <priority>0.8</priority>
    </url>
    ```
  - ✅ 更新完了

- [ ] **Google Search Console 登録**
  - https://search.google.com/search-console へアクセス
  - 「プロパティを追加」
  - ドメイン: `monitor.kikaku-note.com`
  - DNS 設定で所有権確認（TXT レコード追加）
  - ✅ 確認完了

- [ ] **Search Console で URL 検査**
  - Search Console > URL 検査
  - `https://monitor.kikaku-note.com/` を入力
  - ✅ インデックス登録状態確認

- [ ] **Search Console でインデックス登録リクエスト**
  - URL 検査 > 「インデックス登録をリクエスト」ボタンクリック
  - ✅ リクエスト完了（通常 1～2 週間でインデックス）

### バックアップ・同期

- [ ] **NAS へ robocopy**
  - ローカル PC のリポジトリをバックアップ
  - 例：
    ```powershell
    robocopy "C:\Users\<USERNAME>\Projects\kikaku-note.com\repos\kikaku-note-monitor" "\\NAS\backup\kikaku-note-monitor" /MIR /LOG:"C:\robocopy.log"
    ```
  - ✅ バックアップ完了

### 最終確認

- [ ] **全体動作確認**
  - [ ] サイトにアクセス可能
  - [ ] 計算機が動作
  - [ ] スマホで表示確認
  - [ ] GA4 計測中

- [ ] **ドキュメント完成**
  - [ ] README.md 作成
  - [ ] publish-checklist.md 作成
  - [ ] GitHub に Push 完了

---

## 🎉 公開完了！

すべてのチェックが完了しました。以下のリソースを参照してください：

- **サイト**: https://monitor.kikaku-note.com/
- **GitHub**: https://github.com/<USERNAME>/kikaku-note-monitor
- **Cloudflare**: https://dash.cloudflare.com/pages
- **Google Search Console**: https://search.google.com/search-console

---

## 📝 補足

### 今後の更新手順

1. ローカルで `index.html` などを編集
2. Git にコミット: `git commit -am "Update description"`
3. Git にプッシュ: `git push origin main`
4. Cloudflare Pages が自動デプロイ（通常数秒）
5. 新しいコンテンツを Search Console で再度インデックス登録リクエスト

### トラブル対応

**ページが表示されない場合**
- Cloudflare Pages のデプロイ状態確認
- Custom domain の DNS 設定確認
- ブラウザキャッシュクリア

**GA4 が計測されない場合**
- ブラウザコンソール (F12) でエラー確認
- Google Analytics 管理画面で測定 ID 確認

**インデックスされない場合**
- Search Console で再度 URL 検査実行
- robots.txt が正常か確認
- meta robots タグを確認（`index.html` に設定済み）
