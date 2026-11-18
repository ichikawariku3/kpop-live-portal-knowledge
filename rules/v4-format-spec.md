# 本文フォーマットv4 変換仕様（CNBLUE試行で承認済み・全記事展開用）

元ファイル： ~/workspace/kpop-live-portal/v3-bodies/<投稿ID>.html
出力先： ~/workspace/kpop-live-portal/v4-bodies/<投稿ID>.html
見本： ~/workspace/kpop-live-portal/v4-sample-98.html（CNBLUE・公開済み）

## 変換するのは「日程・会場」セクションだけ
現行は h3「日程・会場」の下に、日程・会場・チケット料金・チケット販売期間・URLが入れ子の <ul> で全部ぶら下がっている。これを3つの h3 に分割する。

1. h3「日程・会場」
2. h3「チケット料金（税込）」
3. h3「チケット販売期間」

## 日程・会場の形
- 会場ごとに段落を分ける：<p style="margin-bottom:14px;"><strong>会場名</strong><br>日付・開場・開演の行…</p>（会場の区切りをはっきりさせるため余白を付ける）
- 終了した公演日にはグレーのピルを付ける：
<span style="display:inline-block;padding:1px 8px;border-radius:999px;background:#3f3f46;color:#d4d4d8;font-size:12px;">開催済み</span>
- 「会場：A／B／C」の総括行は、日程ブロックで会場が明示される場合は省略してよい（情報の重複回避）。ただし会場名そのものを落とさないこと。

## チケット料金の形
- 表にする。先頭にヘッダー行（席種／料金）を付ける。書式は見本どおり：
<table style="width:100%;border-collapse:collapse;">
<tr><td style="border:1px solid #4b3a6b;padding:8px 10px;"><strong>席種</strong></td><td style="border:1px solid #4b3a6b;padding:8px 10px;text-align:right;white-space:nowrap;"><strong>料金</strong></td></tr>
<tr><td style="border:1px solid #4b3a6b;padding:8px 10px;">席種</td><td style="border:1px solid #4b3a6b;padding:8px 10px;text-align:right;white-space:nowrap;">金額</td></tr>
</table>
- 席種側のセルに、条件ラベル（、アップグレードシート、名古屋・東京公演のみ、等）は元の文言のまま残す。
- ※で始まる注記は表の外に出し、まとめて
<p style="font-size:13px;color:#b9b3c9;">※…<br>※…</p>
の形にする。

## チケット販売期間の形
- 販売枠ごとに段落：<p><strong>枠の名前</strong> ピル<br>詳細文</p>
- ピルの書式：<span style="display:inline-block;padding:1px 8px;border-radius:999px;背景;color:#fff;font-size:12px;">ラベル</span>
- 受付中／発売中／追加販売決定など「今動いている・前向き」な状態：背景 background:linear-gradient(90deg,#059669,#10b981)
- 受付終了／販売終了：背景 background:#3f3f46、文字色は #d4d4d8（color指定を #d4d4d8 にする）
- 未発表／開始前（予定）：背景 background:linear-gradient(90deg,#1d4ed8,#3b82f6)
- ラベル文は短く（受付中／受付終了／未発表／SOLD OUT／追加販売決定 など）。詳細文に元の情報をすべて残す。
- **ピルは「状態」専用**。「愛知公演のみ」のような対象範囲の注記はピルにせず、通常のテキスト（括弧書きなど）で書く。
- 取扱プレイガイドはこのセクションの最後に：
<p><strong>取扱プレイガイド</strong>：…</p>
- **生URLの行は置かない**。代わりに記事の最後（末尾の※注意書きの後）に、小さな出典行を1行だけ置く：
<p style="font-size:13px;color:#b9b3c9;">出典：<a href="URL">サイト名</a>／<a href="URL">サイト名</a></p>
サイト名は元のURL行の括弧内の名称を使う。ボタンと重なるリンクも、出典としてはこの形で残す。

## ボタン行
- ~/workspace/kpop-live-portal/wave2-buttons.json の該当投稿IDのHTMLを、受付状況サマリー段落（の </p>）の直後にそのまま挿入する。

## English Summary
- 見出しは <h3>English Summary（英語の要約）</h3> とする（日本語読者向けに位置づけを明示）。本文は変えない。

## 変えてはいけないもの
- 導入文、受付状況サマリー、ホテルセクション、English Summary、対バン等の注記段落、末尾の注意書きは v3 から一字一句変えない。
- 日付・時刻・料金・会場名・URLなどの事実は追加・削除・言い換え禁止。構造を変えるだけ。
- 判断に迷う箇所は、変換せず v3 の形のまま残し、作業報告にその箇所を明記する。

## アーティスト名の初出併記（2026-11-16追加）
- 本文でアーティスト名が最初に出る箇所に、カタカナ読みを併記する。ファンの通称が定着している場合は「読み／通称」の形で両方入れる（例：Stray Kids（ストレイキッズ／スキズ）、&TEAM（エンチーム））。
- 表記は正確な音写より、ファンの実際の呼び方を優先する（2026-11-16、陸の指示）。
- 併記は初出の1か所だけ。本文の他の箇所や記事タイトルには入れない。

## アイキャッチの追随ルール（2026-11-18追加、陸の指示）
- 記事の事実（公演数・日程・会場など）が変わって、アイキャッチ画像内の文言と食い違うようになったら、アイキャッチも最新に合わせて作り直す。デザインは既存の生成方式（eyecatch/make_neon.py、チップなし版 neon2）をそのまま使い、文言だけを正しくする。
- 生成スペックの正本は eyecatch/make_all.py の DATA。文言を変えたらスペック側も同じ値に直してから生成する。
- 従来の「既存のアイキャッチは変更しない」は、事実と食い違っていない場合の話。事実変更に伴う追随更新はこのルールが優先する（初適用：&TEAM記事ID102、41公演→42公演）。
