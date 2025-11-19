# GROWI Plugin PDF Viewer

GROWI に添付した PDF をページ内へ埋め込み表示するためのプラグインです。

## 使い方

1. GROWI ページに対象の PDF ファイルを添付します。
2. ページ本文に以下のマクロを記述します。

```markdown
$pdfviewer(/attachment/添付ファイルID,width=100%,height=500px)
```

- `width` と `height` は必須属性です。単位（`px` / `%` など）も忘れずに指定してください。
- `添付ファイルID` には GROWI の添付パス（例: `/attachment/64e0...`）を指定します。

## 日本語PDFの表示について

PDF にフォントが埋め込まれている場合は追加作業なしで日本語が表示されます。フォントが埋め込まれていない PDF でも表示できるよう、PDF.js が利用する CMap および標準フォントデータを CDN からロードする設定をデフォルトで有効にしています。

- オフライン環境などで CDN を利用できない場合は、`pdf.js` の `cmaps` と `standard_fonts` ディレクトリを任意の場所に配置し、`src/pdfviewer.ts` 内の `cMapUrl` / `standardFontDataUrl` をそのパスに変更してください。
- GROWI に Content Security Policy (CSP) を設定している場合は、`cdnjs.cloudflare.com` を `script-src` / `font-src` に追加してください。

## License

MIT

