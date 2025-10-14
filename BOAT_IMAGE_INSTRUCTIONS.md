# 船の画像追加手順

## 必要な作業

このブランチでは、店舗情報セクションに船の画像を追加する準備ができています。
以下の手順に従って、画像ファイルを追加してください。

## 画像ファイルの追加方法

1. **画像の最適化**
   - 提供された船の画像を最適化します
   - 推奨サイズ: 幅 1200px 程度（自動的にレスポンシブ対応されます）
   - ファイル形式: JPG または WebP
   - ファイルサイズ: 500KB以下を推奨

2. **画像の保存**
   ```bash
   # プロジェクトのルートディレクトリに boat.jpg として保存
   cp /path/to/your/boat-image.jpg /home/kusanohisashi/izakayanagomi01/boat.jpg
   ```

3. **ImageMagickを使った最適化（オプション）**
   ```bash
   # インストールされている場合
   convert boat.jpg -resize 1200x -quality 85 boat.jpg
   ```

   または

   ```bash
   # WebP形式に変換（より小さいファイルサイズ）
   convert boat.jpg -resize 1200x -quality 85 boat.webp
   # HTMLファイルで src="boat.webp" に変更する必要があります
   ```

## 実装済みの変更内容

### 1. HTML の変更 ([index.html:562-567](index.html#L562-L567))
- Google マップの下に船の画像を表示するコードを追加
- レスポンシブ対応済み
- 適切な alt テキスト付き

### 2. CSS の変更 ([style.css:1166-1198](style.css#L1166-L1198))
- `.boat-image-container` クラス: 画像コンテナのスタイル
- `.boat-image` クラス: 画像本体のスタイル
  - ホバー効果（拡大＋シャドウ）
  - レスポンシブ対応
  - モバイル表示最適化
- PC: 最大高さ 400px
- スマホ: 最大高さ 300px

### 3. 団体予約情報の追加 ([index.html:536-539](index.html#L536-L539))
- 店舗情報セクションに「団体様もご案内出来ます。」を追加
- 定休日の下に表示

## 表示確認方法

```bash
# ローカルサーバーで確認（Python使用）
cd /home/kusanohisashi/izakayanagomi01
python3 -m http.server 8000

# ブラウザで開く
# http://localhost:8000
```

または

```bash
# 直接ブラウザでファイルを開く
open index.html  # macOS
xdg-open index.html  # Linux
start index.html  # Windows
```

## チェックリスト

- [ ] 船の画像ファイル（boat.jpg）をプロジェクトルートに配置
- [ ] 画像が適切に最適化されている（サイズ・品質）
- [ ] ブラウザで表示確認
- [ ] レスポンシブ表示の確認（PC・タブレット・スマホ）
- [ ] 団体予約情報が正しく表示されている

## 問題が発生した場合

### 画像が表示されない
1. ファイル名が `boat.jpg` になっているか確認
2. ファイルがプロジェクトのルートディレクトリにあるか確認
3. ブラウザのキャッシュをクリアして再読み込み（Ctrl+Shift+R または Cmd+Shift+R）

### 画像サイズが大きすぎる
```bash
# ImageMagickで圧縮
convert boat.jpg -resize 1200x -quality 80 boat-optimized.jpg
mv boat-optimized.jpg boat.jpg
```

### WebP形式を使いたい場合
1. 画像をWebP形式に変換
2. [index.html:564](index.html#L564) の `src="boat.jpg"` を `src="boat.webp"` に変更

## その他の注意事項

- 画像の著作権や使用許諾を確認してください
- SEO用のalt属性は既に設定済みです
- 必要に応じてalt属性のテキストを変更できます
