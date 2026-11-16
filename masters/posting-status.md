# WordPress投稿ステータス（2026-11-11開始）

方式: ブラウザで管理画面（ユーザー kpopliveinjapan）にログインし、コードエディタに本文HTMLを貼って下書き保存。公開は全下書き完了後に公開前チェックを経て実施予定。

- テスト下書き: 投稿ID 79（Muse連携確認用下書き）→ 確認後に削除すること
- BIGBANG: 下書き作成済み 投稿ID 82
- ENHYPEN: 下書き作成済み 投稿ID 84
- 2026 MAMA AWARDS: 下書き作成済み 投稿ID 86
- FNC KINGDOM 2026: 下書き作成済み 投稿ID 88
- Hearts2Hearts: 下書き作成済み 投稿ID 90
- TXT: 下書き作成済み 投稿ID 92
- LE SSERAFIM: 既存ID76を書き換えて下書き化済み（元は公開済み→現在は下書き。公開フェーズで再公開する）
- Kep1er: 下書き作成済み 投稿ID 96
- CNBLUE: 下書き作成済み 投稿ID 98
- NOWZ: 下書き作成済み 投稿ID 100
- &TEAM: 下書き作成済み 投稿ID 102
- NEXZ: 下書き作成済み 投稿ID 104
- Stray Kids: 下書き作成済み 投稿ID 106
- Oh My Girl: 下書き作成済み 投稿ID 108
- MONSTA X: 下書き作成済み 投稿ID 110
- 2NE1 & TEN: 下書き作成済み 投稿ID 112
- NMIXX: 下書き作成済み 投稿ID 114
- ILLIT: 既存ID70を書き換えて下書き化済み（元は公開済み→現在は下書き。公開フェーズで再公開する）
- ATEEZ: 下書き作成済み 投稿ID 117
- FTISLAND: 下書き作成済み 投稿ID 119
- LIGHTSUM: 下書き作成済み 投稿ID 121
- Hi-Fi Un!corn: 下書き作成済み 投稿ID 123
- WayV: 下書き作成済み 投稿ID 125
- ONEUS: 下書き作成済み 投稿ID 127
- NCT WISH: 下書き作成済み 投稿ID 129
- izna: 下書き作成済み 投稿ID 131

## 下書き投稿：全26本完了（2026-11-11）
残作業：テスト下書きID79の削除、公開前チェック（販売状況の再確認）後の公開フェーズ。

## 公開フェーズ（2026-11-11開始）
- テスト下書きID79：ゴミ箱へ移動済み（完全削除はしていない）
- 公開済み（16本）：LE SSERAFIM（ID76、再公開。公開日時は元の3/29のまま）、BIGBANG（ID82）、ENHYPEN（ID84）、MAMA（ID86）、FNC KINGDOM（ID88）、Hearts2Hearts（ID90）、TXT（ID92）、ILLIT（ID70、下記参照）、Kep1er（ID96）、CNBLUE（ID98）、NOWZ（ID100）、&TEAM（ID102）、NEXZ（ID104）、Stray Kids（ID106）、Oh My Girl（ID108）、MONSTA X（ID110）
- ILLIT（ID70）：書き換え保存が下書きに反映されておらず旧テンプレートのまま公開されていたが、自動保存リビジョン116（2026-11-11 16:10）から復元し、タグ・抜粋を再入力して更新・公開完了。公開URLで新内容の表示を確認済み。
- 公開済み（最終バッチ10本）：ONEUS（ID127、公開前にmahocastで期間を再確認し記事と一致）、2NE1 & TEN（ID112）、NMIXX（ID114）、ATEEZ（ID117）、FTISLAND（ID119）、LIGHTSUM（ID121）、Hi-Fi Un!corn（ID123）、WayV（ID125）、NCT WISH（ID129）、izna（ID131）
- **全26本の公開完了（2026-11-11）**
- MUSIC BANK GLOBAL FESTIVAL（ID192）：2026-11-11 公開。URL: https://www.kpopliveinjapan.com/musicbank-global-festival-2026/（カテゴリEVENT、アイキャッチはチップなし版 neon2）。ライブ一覧は全27本表示を確認。必須フォロー：11/16 00:10にプレリザーブ締切後の販売状況を再確認（cron予約済み）、一般発売の発表時に即時更新、追加出演発表時に更新。
- アイキャッチ：2026-11-11、全27本をチップなし版（neon2-*.jpg、対応表 mapping-neon2.json）に差し替え完了。理由は画像内カテゴリチップとサイト側カテゴリラベルの二重表示解消。LE SSERAFIMはタイトル文面のアーティスト名重複も解消。
- デザイン修正（調査ベース）：2026-11-11 反映確認済み。h2見出しは全面グラデーション→ダーク面＋細い帯、全体背景は少し明るいダークグレー寄り、スマホ固定フッターメニュー（ライブ一覧／検索／TOP）有効化。

## v4フォーマット適用（2026-11-12未明完了）
- 全27本の本文を v4-bodies/ の内容に差し替え完了（タイトル・スラッグ・カテゴリ・タグ・アイキャッチは不変）。
- タイトル修正2件：192（MUSIC BANK）末尾の重複「（合同フェス）」を削除し「2026 MUSIC BANK GLOBAL FESTIVAL IN JAPAN（全25組出演の合同フェス）｜12月12日・13日 国立競技場」に。76（LE SSERAFIM）先頭の重複「LE SSERAFIM｜」を削除。
- ライブ一覧（/live-event/）：公演日バッジ・受付状況ピルを廃止し、締切がある公演のみタイトル下に小さく表示。既定の並びは「開催日が近い順」。「受付中のみ」トグル追加（オーバーレイラベル付き16件のみ表示）。オーバーレイラベルは維持。
- 「ピックアップ」タグ：追加CSSで記事ページのタグ欄から非表示（タグ自体とスライダー指定は維持）。
- スマホ固定フッターメニュー：カスタマイザーで表示位置の割り当てを外して無効化（メニュー自体は残存、復旧可能）。
- 後始末：テスト下書きID323はゴミ箱へ、テストメディアID322は完全削除。
- 監査：監査係が公開ページと v4-bodies を照合し、本文27本・タイトル2件は正本どおりと確認（audit-report-v4-20261112.md）。一覧表示・タグ・フッターメニューは適用時の目視確認で担保。

## 枠記事（発表前の受け皿ページ、2026-11-12開始）
方針：検索評価に影響しない範囲で、紹介・直近の日本公演実績・合同イベント出演・公式リンクを入れた実質のあるページにする（陸の承認済み・段階拡大）。
- BABYMONSTER（ID360）：2026-11-12公開 https://www.kpopliveinjapan.com/babymonster/ （カテゴリ ライブ、アイキャッチ neon2-babymonster.jpg、本文の正本は frame-bodies/babymonster.html）
- i-dle（ID363）：2026-11-12公開 https://www.kpopliveinjapan.com/i-dle/ （カテゴリ ライブ、アイキャッチ neon2-idle.jpg、本文の正本は frame-bodies/idle.html）
- ライブ一覧の並び替えデータ（固定ページID63のカスタムHTML内 DATA、形式はスラッグキー→[first_date, アーティスト名]）に2件を first_date="9999-12-31" で追加済み。開催日順では末尾、名前順では名前位置、受付中のみでは非表示になることを確認済み。枠記事を新規公開したら必ず DATA にも同じ形式で追加すること（未追加だと日付なし扱いで先頭に出る）。
- 第2弾13組（BLACKPINK／TREASURE／ZEROBASEONE／aespa／RIIZE／SEVENTEEN／BTS／EXO／SHINee／東方神起／TWICE／ITZY／IVE）は公式調査完了（全組とも単独公演は未発表。調査ファイル frame-research-batch2-a/b/c.md）。
- 第2弾 前半7本：2026-11-12未明に公開完了。BLACKPINK（ID368）https://www.kpopliveinjapan.com/blackpink/ ／TREASURE（ID371）/treasure/ ／ZEROBASEONE（ID374）/zerobaseone/ ／aespa（ID377）/aespa/ ／RIIZE（ID380）/riize/ ／SEVENTEEN（ID383）/seventeen/ ／BTS（ID386）/bts/ 。本文の正本は frame-bodies/、アイキャッチは neon2-<slug>.jpg。
- 第2弾 後半6本：2026-11-12未明に公開完了。EXO（ID389）/exo/ ／SHINee（ID392）/shinee/ ／東方神起（ID395）/tvxq/ ／TWICE（ID398）/twice/ ／ITZY（ID401）/itzy/ ／IVE（ID404）/ive/（スラッグは ive のまま確定）。これで枠記事は全15本公開完了。
- JxJ記事：2026-11-12未明に公開完了。投稿ID 407、https://www.kpopliveinjapan.com/jxj-journey-into-dreaming-japan/（カテゴリ ライブ、タグ JxJ／SEVENTEEN、アイキャッチ neon2-jxj-journey-into-dreaming-japan.jpg、本文の正本は draft-jxj-v4.html）。SEVENTEEN枠記事（ID383）の「メンバーソロ・ユニット公演」段落末尾にJxJ記事へのリンク文を追加済み。
- ライブ一覧DATA：枠15本を first_date=9999-12-31 で、JxJを ["2026-11-21","JXJ"] で追加済み。JxJは LABELS に「チケット発売中」で追加。枠15本のカードには「公演未発表」のグレーピル（#6b7280）を表示（実装はカスタマイザー追加CSSの figure::after、スラッグ別指定）。確認済み：開催日順で枠は末尾（Stray Kidsの後）、「受付中のみ」で枠は非表示、JxJは先頭付近に発売中ラベル付き。注意：固定ページID63内には表示に使われていない旧JS（T／U／TEST）と .live-tbd-label 用CSSのデッドコードが残っている（未削除）。
- 公開済み投稿は合計43件になった（公演27＋枠15＋JxJ1）。
- 監査（audit-report-frames-jxj-20261112.md）で要修正4件：BTSのEnglish Summaryのカンマ欠落（中継時の落ち）、BLACKPINK／TWICE／ITZYのツアー名の半角＜＞がタグとして解釈され表示欠落。正本ファイル（frame-bodies）を全角＜＞に修正済み。公開ページ側は2026-11-12朝、陸の承認を得て管理者で修正し、公開ページで表示を確認済み。これで新規16本は監査合格となった。

## ソロ／ユニット記事（2026-11-12公開）
方針変更（2026-11-12、陸の決定）：チケット販売が動いているソロ／ユニット公演は、グループ公演と同様に通常記事として独立させる。いずれも通常パイプライン（探す係→チェック→監査→投稿判断係「投稿可」）を経て公開。
- チャンミン（ID449）：2026-11-12公開 https://www.kpopliveinjapan.com/changmin-second-dining-japan-2027/ （カテゴリ ライブ、タグ チャンミン／東方神起、アイキャッチ neon2-changmin-second-dining.jpg、本文の正本は draft-changmin-v4.html）
- ユンホ（ID458）：2026-11-12公開 https://www.kpopliveinjapan.com/yunho-project26-scene1-japan/ （カテゴリ ライブ、タグ ユンホ／東方神起、アイキャッチ neon2-yunho-project26.jpg、本文の正本は draft-yunho-v4.html）
- YESUNG（ID447）：2026-11-12公開 https://www.kpopliveinjapan.com/yesung-10th-anniversary-tour-japan-2027/ （カテゴリ ライブ、タグ YESUNG／SUPER JUNIOR、アイキャッチ neon2-yesung-10th-anniversary.jpg、本文の正本は draft-yesung-v4.html）
- SUPER JUNIOR-83z（ID451）：2026-11-12公開 https://www.kpopliveinjapan.com/superjunior-83z-fancon-1983-osaka/ （カテゴリ ライブ、タグ SUPER JUNIOR-83z／SUPER JUNIOR、アイキャッチ neon2-superjunior83z-1983.jpg、本文の正本は draft-83z-v4.html）
- Jang Wooyoung（ID456）：2026-11-12公開 https://www.kpopliveinjapan.com/jang-wooyoung-concert-japan-2026/ （カテゴリ ライブ、タグ Jang Wooyoung／2PM、アイキャッチ neon2-jangwooyoung-concert.jpg、本文の正本は draft-wooyoung-v4.html）
- 東方神起枠記事（ID395、/tvxq/）：本文を frame-bodies/tvxq.html の内容に更新済み（ユンホ・チャンミン両ソロ記事へのリンク追加、Bigeast2次先行の記述を現況に修正）。
- ライブ一覧DATA：5件を追加済み（チャンミン ["2027-02-22","CHANGMIN"]／ユンホ ["2026-11-14","U-KNOW"]／YESUNG ["2027-02-12","YESUNG"]／SUPER JUNIOR-83z ["2026-12-22","SUPER JUNIOR-83Z"]／Jang Wooyoung ["2026-12-25","JANG WOOYOUNG"]）。LABELS は YESUNG／SUPER JUNIOR-83z／Jang Wooyoung の3件を「チケット発売中」で追加（チャンミン・ユンホはラベルなし）。
- 公開済み投稿は合計48件になった（公演32＋枠15＋JxJ1）。

## 必須フォロー更新（2026-11-12）
- FNC KINGDOM（ID88）：一般販売（11/12 19:00開始）のプレイガイド確認を実施。公式告知本文でチケットぴあ／ローソンチケット／e+（イープラス）の3社と販売URLを確認し、各販売ページで販売中を確認。記事を受付状況サマリー11/12時点・バッジ「販売中」・購入ボタン3件・ガイド別受付終了日時に更新し、公開ページで検証済み。正本は v4-bodies/88.html（バックアップ 88.html.bak-20261112）。詳細は goals/k-pop-live-portal-updates/hidden_files/fnc-kingdom-guide-check-20261112.md。

## デザイン修正（2026-11-12未明、管理者で実施）
すべてカスタマイザー「追加CSS」への追記で実施（ロールバックは追加ブロック「2026-11-12 追加修正（管理者・デザイン一式）」以降を削除）。
- 白い帯：html背景を #101018 に統一。トップページは上部・スクロール時とも解消。ヘッダーは .l-header を #111119 単色＋内側 transparent にし、二色の段差も解消。
- ヒーロー：メインビジュアル（PC／SP両方）を hero-a-brand-glow.jpg（アップロード済み https://www.kpopliveinjapan.com/wp-content/uploads/2026/11/hero-a-brand-glow.jpg）に差し替え。キャッチコピーは不変。
- 検索フォーム：入力欄と「検索」ボタンの高さを44pxに統一。見出しバー「KPOP来日公演まとめ」のピンク線のはみ出しを解消。
- 文字コントラスト：body #f2f2fa／main #ececf6 に引き上げ、記事内※注記・出典行は #cfc9dd 程度に明るくした。
- 「ライブ一覧を見る」ボタン：紫→ピンクのグラデーション＋白文字のピル型に統一。
- サイトアイコン：確認したところKバッジ（cropped-logo-badge.png）が設定済みだった。検索結果でWordPressアイコンに見えたのはGoogle側のキャッシュが理由（サイト側は正常）。
- **未解消2件**（当時）：①両カラムの上端揃え（見出しバーが検索フォームより約25〜40px低いまま。CSSで持ち上げを試みたが想定どおり動かず原因未特定。副作用で見出しバー下の余白が広め）②記事ページでスクロールした際、固定ヘッダーの左右端に白い帯が戻る（トップは解消済み。固定ヘッダーの別ラッパーが原因とみられるが未特定）。
- **残件2件の解消（2026-11-12 04:08、管理者・追加CSSのみ）**：①原因は見出しh2が入るフルワイドブロック（TOP固定ページID47の先頭ブロック）の pc-pt-24（上パディング24px）で、前回の `main > h2` セレクタはそもそも一致していなかった。持ち上げ規則（top:-143px等）を全削除し、`main .swell-block-fullWide:first-child{padding-top:0!important;}` を追加。幅1919px実測で上端の差は31〜32px→0〜1pxに解消（幅1280pxは直接実測なし、固定24px除去のため残差は小さい見込み）。②実測ではトップページのスクロール時にも白帯が出ていた（前回報告の前提が誤り）。固定ヘッダーの全幅ラッパー／疑似要素が原因で、`[class*="header"]`／`[class*="fix"]`／`[id*="header"]`／`[id*="fix"]` とその ::before/::after の背景を #111119 に統一する規則を追加。トップ・記事ページとも上部／スクロール時に全幅 #111119 を実測確認。ロールバックは追加CSS末尾のコメント「2026-11-12 残件1」「2026-11-12 残件2」の規則を削除。副作用：ページトップボタン（右下↑）が白い円から暗色の円（紫の細枠・白矢印）に変化（機能は不変）。注意：ConoHa側のキャッシュ削除はパネルが表示できず未実施（WEXALはOFF）。匿名表示の確認はキャッシュバスト付き再読み込みで実施。
- 注意（2026-11-12判明）：保管庫は kpopliveinjapan.com のログインを1件しか保持できず、muse の保存で管理者ログインが上書きされた。管理者作業の前には保管庫の内容がどちらのアカウントか確認すること（切り替えには陸による再保存が必要）。

## ONEW記事（2026-11-14公開）
- ONEW（ID508）：2026-11-14公開 https://www.kpopliveinjapan.com/onew-the-live-japan-2027/ （カテゴリ ライブ、タグ ONEW／SHINee、アイキャッチ neon2-onew-the-live-japan-2027.jpg、本文の正本は draft-onew-v1.html）。通常パイプライン（一次・最終・整合成・人の視点・監査）＋投稿判断係「投稿可」を経て、陸の承認により管理者で公開。
- ライブ一覧（固定ページID63）：DATA に "onew-the-live-japan-2027":["2027-01-14","ONEW"]、CARDTITLES に "onew-the-live-japan-2027":"ONEW ［ONEW THE LIVE］" を追加済み。トップページ（ID47）のスライダー側CARDTITLESにも同日に追加済みで、スライダー表示確認のため投稿508に「ピックアップ」タグを付与（タグは ONEW／SHINee／ピックアップ）。その結果、スライダー（ピックアップ最新8件）からBIGBANGが枠外に回った。
- SHINee枠記事（ID392、/shinee/）：本文末尾の出典直後に「ソロコンサート：」として ONEW記事へのリンクを追記済み。
- 公開済み投稿は合計49件になった（公演33＋枠15＋JxJ1）。

## Young K記事（2026-11-14公開）
- Young K（ID530）：2026-11-14公開 https://www.kpopliveinjapan.com/youngk-youngest-japan-2027/ （カテゴリ ライブ、タグ Young K／DAY6、アイキャッチ neon2-youngk-youngest.jpg、本文の正本は draft-youngk-v1.html）。Young K Solo Tour ＜YOUNGEST＞ in JAPAN、2027年2月13日（土）・14日（日）東京体育館 メインアリーナ、全席指定15,000円。最速先行・2次先行・プレイガイド先行はすべて終了、一般発売は公式未発表（定価トレード実施予定）。通常パイプライン（一次・整合成・人の視点・監査）＋投稿判断係「投稿可」を経て、編集者 muse で公開。公開後に公開ページと正本の全項目一致を確認済み。
- ライブ一覧（固定ページID63）：DATA に "youngk-youngest-japan-2027":["2027-02-13","YOUNG K"]、CARDTITLES に "youngk-youngest-japan-2027":"Young K ソロツアー ＜YOUNGEST＞" を追加済み。トップページ（ID47）のスライダー側CARDTITLESにも同日追加済み。一覧で開催日順の正しい位置（YESUNGとCHANGMINの間）に表示されることを確認済み。
- 必須フォロー：一般発売が公式発表されたら即時に記事更新（サマリー／ピル／販売期間／English Summary／一覧ラベル）。
- 公開済み投稿は合計50件になった（公演34＋枠15＋JxJ1）。

## 記事更新（2026-11-14、管理者で実施・陸承認）
- ユンホ（ID458）：大阪城ホール公演の機材席開放先着受付（東方神起公式 2026-11-13発表、mu-mo TICKET、14日公演は11/14 14:00締切・15日公演は11/15 13:00締切）を反映。本文正本 draft-yunho-v4.html の更新版をそのまま差し替えて 10:17 に更新、公開ページで「受付中」ピルと11/14時点サマリーを確認。
- Kep1er（ID96）：ぴあ一般販売の再開（〜11/21 23:59）に合わせて文言8件を修正（受付状況ラベル11/14時点、メンテ休止の未来形→終了・再開済み、ぴあ注記を11/21まで受付中に、直筆サイン入りポスター抽選は「対象でした（購入期間は終了）」と明記、English Summaryも同様）。10:20更新、公開ページで確認。なおローカル正本 draft-kep1er-final.md は旧文のままなので、次回編集時はライブ側を正とすること（置換内容の記録は goals/k-pop-live-portal-updates/hidden_files/kep1er-pia-recheck-20261114-progress.md）。

## 必須フォロー更新（2026-11-16）
- Jang Wooyoung（ID456）：Hottest Japan Mobile先行（〜2026-11-15 23:59）締切後の再確認を実施。特設サイト・FCニュース・申込ページ（汎用ページへ転送）で、締切以外の新規発表（プレイガイド先行・一般発売・当落日時）がないことを確認。記事を2026年11月16日時点・全FC先行受付終了に更新（サマリー／Mobileピル受付終了／申込ボタン削除／プレイガイド段落／English Summary）。管理者で更新し、公開ページとライブ一覧の「受付終了」ラベルを再読み込みで確認済み。ticket_deadline は 9999-12-31 23:59 に設定、ピックアップタグは当初から付いておらずスライダー外を確認。正本は draft-wooyoung-v4.html（更新済み）、詳細は goals/k-pop-live-portal-updates/hidden_files/wooyoung-mobile-recheck-20261116.md。
- Hi-Fi Un!corn（ID123）：RaSiDo先行・FNCオフィシャル先行（いずれも〜2026-11-15 23:59）締切後の再確認を実施。公式サイトNEWS一覧（最新11/9付のまま）・news_436・news_440で、締切以外の新規発表（プレイガイド先行・一般発売・公式リセール）がないこと、当落発表11/19 18:00頃〜・入金期間〜11/25 23:59に変更がないことを確認。記事を2026年11月16日時点・両先行受付終了に更新（サマリー／両先行ピル受付終了／一般発売・リセールの時点表記／English Summary）。管理者で更新し、公開ページ・トップスライダー外・ライブ一覧の「受付終了」ラベルと「受付中のみ」非表示（オン時20件）を再読み込みで確認済み。ticket_deadline は 9999-12-31 23:59 を新規設定、ピックアップタグは当初から付いておらずスライダー外を確認。ライブ一覧BADGEは「現在受付なし・一般発売は未発表」、ONSALE→ENDED同期も完了。正本は v4-bodies/123.html と draft-hifiunicorn-final.md（いずれも更新済み）、詳細は goals/k-pop-live-portal-updates/hidden_files/hifiunicorn-presale-recheck-20261116.md。
- &TEAM（ID102）：アリーナ公演 LUNÉ Membership（JP）会員先行（〜2026-11-15 23:59）締切後の再確認を実施。公式告知・NEWS一覧で当落・入金期間（11/24 11:00〜11/29 23:00）に変更がないこと、アリーナ一般発売など新規受付の発表がないことを確認。記事を2026年11月16日時点に更新（サマリー／JP先行ピルを受付終了に／English Summary）。ホール公演の一般発売中と「チケット発売中」ラベルは維持。管理者で更新し公開ページで確認済み。ticket_deadline は未設定だったため 2026-11-29 23:59（GL先行抽選受付締切）を新規設定、ライブ一覧BADGEは「一般発売中／アリーナGL先行は11/29締切」に更新。正本は v4-bodies/102.html・draft-andteam-final.md（更新済み）、詳細は goals/k-pop-live-portal-updates/hidden_files/andteam-presale-recheck-20261116.md。所見：トップスライダーに&TEAMは作業前から未掲載（ピックアップタグ無し）、ライブ一覧の締切表示は全カードで出ておらずスクリプト側の別途確認が必要。
