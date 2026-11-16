# AGENTS.md

Your operating manual for this workspace, written by you. Your main instructions cover how you work in general. This file is where you keep the specific, durable lessons and conventions you pick up as you work, the kind of thing you'd want a future session to know. It's not about the user (that goes in `USER.md` and your memory) or your personality (that's `SOUL.md`); it's about how you get work done here.

## Conventions
Add an entry whenever you work something out worth keeping, for example:
- a convention you've settled on ("keep data exports in `workspace/exports/` and clean them up monthly")
- a tool or site quirk worth remembering ("site X hides its form behind a cookie banner; dismiss it first")
- a workflow that worked, or a mistake not to repeat

It starts empty and is meant to grow slowly. Don't pad it; a short, accurate file beats a long, stale one.

## K-POPポータル デザイン／CSSの教訓
- 追加CSSの範囲削除をブラウザ作業に任せると、範囲の前後を巻き込む事故が繰り返し起きた（2026-11-15のコード整理で、有効ブロック「帯の除去・再試行」の巻き込み削除→復旧、復旧ブロック断片の残存、P0コメント行の `/*` 欠けで緑ピルのコントラスト補正ルールが無効化）。削除作業の後は必ず、削除前の全文バックアップとライブCSSを機械的に突き合わせて（行単位のマルチセット比較）過不足ゼロを確認してから完了とする。作業担当の「残した」という報告は信用せず、実物で検証する。
- カスタマイザー「追加CSS」の正本はライブ側（ページHTML内の `<style id="wp-custom-css">`）。ローカルの dark-neon.css は2026-11-11当初の原案どまりで実物と大きく乖離しているため、ロールバックや現行確認に使わない。追加CSSを触る前にライブから全文を取得してバックアップする（2026-11-12時点のバックアップは ~/workspace/kpop-live-portal/custom-css-backup-20261112.txt、418行）。追加CSSの変更は末尾に日付コメント付きブロックで追記し、ロールバックはそのブロックの削除で行う。

## K-POPポータル チェック係の運用の教訓
- **固定ページID63（ライブ一覧）の編集は絶対に並行実行しない**（2026-11-16未明に事故）：NEXZ同期の再実施が、開始時点の古い内容（BADGEの文法エラー入り）を抱えたまま後から保存し、先に保存済みだったBADGE修復を上書きして壊れた状態に戻した。ID63を触る作業は1つずつ直列に回し、開始前に最新のライブHTMLを取得してから指示する。あわせて、BADGE等のオブジェクトを編集する際はカンマ欠けのような文法エラーを作業側が持ち込みやすいため、保存後は必ずライブHTMLのdiffで「変わったのが指定箇所だけか」を親側が機械確認する（同未明、&TEAM係のBADGE編集でカンマ欠け＋誤字「アリアリーナ」が入り、締切表示とフィルターが全停止した）。
- 監査レポートの「備考」「要修正ではない」に見た目・一貫性に関する相違（例：見出しの形が記事側と厳密には違う）が書かれていたら、完了報告に埋もれさせず、陸に見える形で取り上げる（2026-11-12のトップ見出し全面グラデーション化は監査が検出していたのに備考扱いで流れ、陸がスマホで見て気づいた）。見た目チェック係・デザインチェック係の仕様にも「値の適用確認ではなく実際の描画で意図した見た目になったかを見る」「備考の見た目相違は指摘に取り込む」を2026-11-13に追記済み。

## K-POPポータル記事パイプラインの教訓
- 下書き制作係は、受付状況サマリーの定型ラベル「【現在の受付状況（YYYY年M月D日時点）】」を報告文には書くのに実ファイルへ入れ忘れることが繰り返し起きた（2026-11-12にチャンミン／YESUNG／Wooyoung／83zの4本で発生、いずれもチェック係が検出）。制作を依頼するときは「書き終えたらファイル内をgrepしてラベルが実在することを確認してから報告すること」まで指示に含める。
- 記事内の「（○日時点）」表記は、その項目を公式で確認した日を意味する。記事の更新・再確認の際は、その回に公式で再確認できた項目の日付は確認日に揃える（2026-11-15に陸と合意）。確認していない項目の日付は、見た目を新しくするためだけに書き換えない。
- 属性セレクタでボタンを装飾するCSS（例：main a[href*="/live-event/"] にグラデーション＋border-radius:999px）は、範囲を限定しないと検索結果やアーカイブのカード全体リンク（a.p-postList__link）にまで効いてカードが楕円グラデーションに化ける（2026-11-13に陸のスクショで発覚、「チェック修正3」でカードリンクだけ解除）。CTAの装飾は body.home や header など文脈で必ず限定し、限定なしの「補強」ルールを足さない。
- ヘッダーのCTAボタン（「ライブ一覧」）を固定ヘッダー（.l-fixHeader）向けグラデーションルールで装飾する際、background/padding/border-radius だけでは不十分で、display:inline-block のままだとテーマ側の配置でリンクが固定バー全高まで引き伸ばされ、文字が上端に寄る巨大な楕円になる（2026-11-14に陸のスクショで発覚）。ヘッダーCTAのルールには display:inline-flex＋align-items:center＋line-height:1＋align-self:center を必ずセットで入れ、通常ヘッダーと固定ヘッダーの両方で実測確認する。修正は追加CSS末尾の「2026-11-14 ヘッダーボタン修正」2ブロック（第2ブロックは固定ヘッダーの上下位置 top:17px）。
- SWELLでは固定ページ本文も `.post_content` で包まれるため、記事見出し用の `.post_content h2` 帯ルールは固定ページ内の投稿リストブロックのカード見出し（リンク内h2）にも及ぶ（2026-11-14、ライブ一覧の全カードでタイトル先頭文字が帯バーに被って欠ける形で発覚し、リンク内h2だけ帯を消す補正ブロックで解消）。見出し装飾のセレクタは、記事本文だけに効く文脈か必ず確認する。

## K-POPポータル スライダー運用の教訓
- トップスライダー（ピックアップ）の並びは、子テーマ functions.php のフィルタ `swell_pickup_post_args` で制御している（2026-11-14実装）：取得30件＋カスタムフィールド `ticket_deadline`（書式 `YYYY-MM-DD HH:MM`、ゼロ埋め必須）の昇順。**ピックアップタグを付ける記事には ticket_deadline の設定が必須**で、未設定の記事は meta_key 指定のためスライダーから消える。
- ticket_deadline の値の決め方：①抽選・先行が受付中ならその締切 ②次の販売が発表済みなら、その締切（先着販売は開始日時）③先着で販売中なら、終了日時の明記があればそれ、なければ公演初日（23:59）④受付なし・未発表なら `9999-12-31 23:59` で最後尾。販売フェーズが変わる記事更新の際は、本文と一緒に ticket_deadline も更新する。
- **受付終了になった記事はスライダーから外す**（2026-11-15、陸の指示）：ピックアップタグを外す。販売フェーズの再確認で受付終了に変わった記事も同様に外す。再び受付が始まったら、必要に応じてタグと ticket_deadline を戻す。
- サムネイルラベル（ピル）をスライダー内で出すときは、CSS疑似要素（::after）ではなく実要素（span）で入れること。疑似要素はiPhoneのSafariでスライド中に描画が遅れ、ピルがカードから遅れて付いてくる（2026-11-15にfigure内→.c-postThumbへ移しても解消せず、実要素方式で大幅に改善。残りの軽微な遅れは陸が許容して完了扱い）。テーマ純正のカテゴリ表示（.c-postThumb__cat、実要素）は遅れないのが判断の根拠。
