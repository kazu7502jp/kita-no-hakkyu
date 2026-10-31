# 北の白球新聞社（リポジトリ）

北海道の中学軟式野球の日刊紙『北の白球新聞』を毎朝発行するためのリポジトリ。
クラウドのルーティンが毎朝6時（日本時間）にこのリポジトリで作業し、GitHub Pages で公開する。

必ず先に読む：`会社概要.md`、`情報源.md`、`編集方針.md`、`発行記録.md`

## ファイル構成
- `issues/YYYY-MM-DD.html` … 各号（完全なHTML文書。フッターのバックナンバーリンクは `../archive.html`）
- `index.html` … 最新号のコピー（フッターのリンクだけ `archive.html` に置き換える）
- `archive.html` … バックナンバー一覧（新しい号を `<ul>` の先頭に追加）
- `発行記録.md` … 号数・日付・一面見出しの表

## 発行手順（毎朝）
1. 日付は日本時間で決める：`TZ=Asia/Tokyo date +%F`
2. 編集方針.md に従って取材・執筆・校閲し、最新号の `<style>` と構造を流用して `issues/<今日>.html` を作る
3. `index.html` を今日の号で置き換え（`../archive.html` → `archive.html`）
4. `archive.html` と `発行記録.md` に追記
5. `git add -A && git commit -m "第N号 YYYY-MM-DD 発行"` して main に push

## PDFを読むとき
WebFetch の結果に「saved to <パス>」と出たら、そのパスを Read で開くと画像として読める。
Read で読めない場合は `pip install pypdf` か `pdftotext` でテキスト化を試す。読み取れない数字は載せない。
