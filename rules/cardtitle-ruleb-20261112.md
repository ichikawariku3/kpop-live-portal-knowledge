# ルールA（cardTitle）作成・登録 ＋ ルールB棚卸し 結果（2026-11-12）

計画書：design-fix-plan-20261112.md Part 2 に対応するファイル側作業の結果。
本作業では WordPress 側の変更は行っていない（live-list-data.json の更新と棚卸しのみ）。

---

## 作業1：cardTitle の作成と登録（ルールA）

### 実施内容
- 着手前に `live-list-data.json` を `live-list-data-backup-20261112.json` として複製（ロールバック用）。
- 全48件について、計画書のルール文案（「アーティスト名 ＋ 公演を一言で表す核の語」、最大28文字・全角換算、日程と会場名は入れない、合同公演は合同と分かる語を含める）に従って cardTitle を作成。
- 登録形式：既存エントリ（48件の投稿オブジェクト配列）は一字も変更せず、ファイルのトップレベルをオブジェクト化して `posts`（既存配列そのまま）と `cardTitles`（slug→cardTitle の対応）を併記した。既存の `label` フィールド（3件）も保持されていることを再読み込みで検証済み。
  - 注意：一覧ページ（固定ページID63）の表示側JSがこの正本を参照する際は、`cardTitles[slug]` を引く形の小改修が必要（本日の別作業で実施予定のJS改修側の申し送り）。
- 文字数は全角換算（半角＝0.5）で全件28文字以内（最大は Hearts2Hearts の21.5文字）。

### 判断メモ
- LE SSERAFIM：計画書の例「LE SSERAFIM 京セラドーム公演」は会場名を含むが、ルール3（会場名は入れない）を優先し、ツアー名を核にした「LE SSERAFIM 'PUREFLOW'」とした。
- 合同イベントの扱い：MUSIC BANK は「（合同フェス）」、FNC KINGDOM は「（合同ライブ）」、2NE1 & TEN は「（合同）」を付与。2026 MAMA AWARDS は計画書が完成形として例示しているため、そのまま「2026 MAMA AWARDS」とした（授賞式イベント）。
- 枠記事15件はすべて「{アーティスト名} 日本公演情報」の形に統一。表記は正式表記に合わせた（aespa／SHINee／東方神起 など）。

### cardTitle 一覧（全48件）

#### 公演記事（33件）

| ID | アーティスト | slug | cardTitle | 全角換算 |
|---|---|---|---|---|
| 100 | NOWZ | nowz-1st-fan-meeting-tokyo | NOWZ 初ファンミーティング | 12.5 |
| 102 | &TEAM | andteam-mark-on-you-japan | &TEAM 'Mark on You' ツアー | 13.0 |
| 104 | NEXZ | nexz-saucin-the-world-japan-2027 | NEXZ SAUCIN' THE WORLD | 11.0 |
| 106 | Stray Kids | stray-kids-run-it-japan-stadium-2027 | Stray Kids RUN IT スタジアム公演 | 16.0 |
| 108 | OH MY GIRL | oh-my-girl-fanmeeting-2026-toyosu | OH MY GIRL ファンミーティング | 14.5 |
| 110 | MONSTA X | monstax-the-x-nexus-encore-japan-2026 | MONSTA X THE X: NEXUS アンコール | 16.0 |
| 112 | 2NE1 & TEN | 2ne1-ten-special-live-2026 | 2NE1 & TEN スペシャルライブ（合同） | 17.5 |
| 114 | NMIXX | nmixx-showcase-2026-aichi | NMIXX 日本デビューショーケース | 15.0 |
| 117 | ATEEZ | ateez-zero-to-all-japan-2027 | ATEEZ ZERO TO ALL | 8.5 |
| 119 | FTISLAND | ftisland-christmas-mini-concert-2026 | FTISLAND クリスマスミニコンサート | 16.5 |
| 121 | LIGHTSUM | lightsum-reidol-showcase-2026 | LIGHTSUM Re:idol ショーケース | 14.5 |
| 123 | Hi-Fi Un!corn | hifi-unicorn-telescope-tokyo-2026 | Hi-Fi Un!corn TELESCOPE 追加公演 | 16.0 |
| 125 | WayV | wayv-born-this-way-japan-2027 | WayV BORN THIS Way | 9.0 |
| 127 | ONEUS | oneus-full-moon-tokyo-2027 | ONEUS FULL MOON | 7.5 |
| 129 | NCT WISH | nctwish-into-the-wish-japan-2027 | NCT WISH INTO THE WISH | 11.0 |
| 131 | izna | izna-who-dat-girl-japan-2027 | izna WHO DAT GIRL? | 9.0 |
| 192 | MUSIC BANK GLOBAL FESTIVAL | musicbank-global-festival-2026 | MUSIC BANK GLOBAL FESTIVAL（合同フェス） | 20.0 |
| 70 | ILLIT | illit | ILLIT 'PRESS START' アンコール | 15.0 |
| 76 | LE SSERAFIM | le-sserafim | LE SSERAFIM 'PUREFLOW' | 11.0 |
| 82 | BIGBANG | bigbang-xx-cosmos-japan-2026 | BIGBANG ＜XX: COSMOS＞ | 11.0 |
| 84 | ENHYPEN | enhypen-blood-saga-japan | ENHYPEN 'BLOOD SAGA' | 10.0 |
| 86 | 2026 MAMA AWARDS | mama-awards-2026-osaka | 2026 MAMA AWARDS | 8.0 |
| 88 | FNC KINGDOM 2026 | fnc-kingdom-2026-yokohama | FNC KINGDOM 2026（合同ライブ） | 15.0 |
| 90 | Hearts2Hearts | hearts2hearts-ready-s2u-ariake | Hearts2Hearts 初ファンイベント 'READY! S2U' | 21.5 |
| 92 | TOMORROW X TOGETHER | txt-steal-the-wind-japan-2026 | TOMORROW X TOGETHER ＜STEAL THE WIND＞ | 19.0 |
| 96 | Kep1er | kep1er-fancon-2026-tokyo | Kep1er FAN-CON [RSVP] | 10.5 |
| 98 | CNBLUE | cnblue-autumn-tour-2026-full-circle | CNBLUE AUTUMN TOUR -FULL CIRCLE- | 16.0 |
| 407 | JXJ | jxj-journey-into-dreaming-japan | JxJ JOURNEY INTO [DREAMING] | 13.5 |
| 447 | YESUNG | yesung-10th-anniversary-tour-japan-2027 | YESUNG 10TH ANNIVERSARY TOUR | 14.0 |
| 449 | CHANGMIN | changmin-second-dining-japan-2027 | CHANGMIN The Second Dining | 13.0 |
| 451 | SUPER JUNIOR-83Z | superjunior-83z-fancon-1983-osaka | SUPER JUNIOR-83z FAN-CON [1983] | 15.5 |
| 456 | JANG WOOYOUNG | jang-wooyoung-concert-japan-2026 | Jang Wooyoung ソロコンサート | 14.0 |
| 458 | U-KNOW | yunho-project26-scene1-japan | U-KNOW PROJECT 26: SCENE ♯1 – EDIT | 17.0 |

#### 枠記事（15件・公演未発表）

| ID | アーティスト | slug | cardTitle | 全角換算 |
|---|---|---|---|---|
| 360 | BABYMONSTER | babymonster | BABYMONSTER 日本公演情報 | 12.0 |
| 363 | i-dle | i-dle | i-dle 日本公演情報 | 9.0 |
| 368 | BLACKPINK | blackpink | BLACKPINK 日本公演情報 | 11.0 |
| 371 | TREASURE | treasure | TREASURE 日本公演情報 | 10.5 |
| 374 | ZEROBASEONE | zerobaseone | ZEROBASEONE 日本公演情報 | 12.0 |
| 377 | AESPA | aespa | aespa 日本公演情報 | 9.0 |
| 380 | RIIZE | riize | RIIZE 日本公演情報 | 9.0 |
| 383 | SEVENTEEN | seventeen | SEVENTEEN 日本公演情報 | 11.0 |
| 386 | BTS | bts | BTS 日本公演情報 | 8.0 |
| 389 | EXO | exo | EXO 日本公演情報 | 8.0 |
| 392 | SHINEE | shinee | SHINee 日本公演情報 | 9.5 |
| 395 | TVXQ | tvxq | 東方神起 日本公演情報 | 10.5 |
| 398 | TWICE | twice | TWICE 日本公演情報 | 9.0 |
| 401 | ITZY | itzy | ITZY 日本公演情報 | 8.5 |
| 404 | IVE | ive | IVE 日本公演情報 | 8.0 |

---

## 作業2：ルールBの棚卸し（既存48件のアイキャッチ文字量）

### 判定方法
- 対象は mapping-neon2.json の全48件。
- neon2 の画像構造は「アーティスト名（大・1行）＋ 公演タイトル（中）＋ 日程・会場メタ（小）」が標準形。ルールBの上限（原則アーティスト名1行・上限2行）に照らし、文字量の判定は「タイトル行数」を主軸にした（メタ行とサイト名は全件共通の補助要素のため判定から除外）。
- 生成時の表示名・タイトル文字列（make_all.py の DATA 等）で机上判定し、境界ケースは実画像を目視確認した（実画像確認：14件＝MUSIC BANK／TXT／NCT WISH／LIGHTSUM／BIGBANG／WayV／NEXZ／Hi-Fi Un!corn／MONSTA X／2NE1 & TEN／BABYMONSTER／JxJ／SUPER JUNIOR-83z／YESUNG）。

### 結果サマリー
- **範囲内：41件**（内訳：公演記事21件＝タイトル1行の標準形、枠記事15件＝アーティスト名＋定型サブ「日本公演・ライブ情報」等で主題2行相当、ソロ5件＝アーティスト名＋タイトル1行）
- **候補リスト入り：7件**（下記。タイトルが2行に折れており、主題テキストが「アーティスト名1行＋タイトル2行」となっているもの。本日は画像を変更しない）

### 将来差し替える場合の候補リスト（7件）

| ID | アーティスト | ファイル | 状況 |
|---|---|---|---|
| 192 | MUSIC BANK GLOBAL FESTIVAL | neon2-musicbank-global-festival-2026.jpg | タイトル2行。2行目は説明文言「全25組出演の合同フェス」で、ルールB文案1（公演名・状態文言は入れない）にも最も抵触する |
| 104 | NEXZ | neon2-nexz-saucin-the-world-japan-2027.jpg | タイトル2行に加えメタも2行に折れ、最下行「他」が画像下端にかかっている。文字量は全件中最多クラス |
| 82 | BIGBANG | neon2-bigbang-xx-cosmos-japan-2026.jpg | タイトル2行（"IN JAPAN" が2行目に落下） |
| 125 | WayV | neon2-wayv-born-this-way-japan-2027.jpg | タイトル2行（同上） |
| 129 | NCT WISH | neon2-nctwish-into-the-wish-japan-2027.jpg | タイトル2行（ツアー名が長い） |
| 121 | LIGHTSUM | neon2-lightsum-reidol-showcase-2026.jpg | タイトル2行（日本語説明文を含む長いタイトル） |
| 407 | JxJ | neon2-jxj-journey-into-dreaming-japan.jpg | タイトル2行（"JEONGHAN X JOSHUA JOURNEY INTO [DREAMING] - JAPAN"） |

### 補足
- 候補7件はいずれも「タイトル文字列が長い」ことが原因で、差し替える場合はルールB（アーティスト名1行のみ）で再生成すれば解消する。ただし既存画像の変更はオーナー指示により行わないため、本リストは将来の差し替え判断用に留める。
- なお、標準形の公演記事（タイトル1行組）も新ルール厳密適用では「タイトル・メタを入れない」に反するが、これは neon2 世代の標準仕様であり、棚卸しの対象は「上限（2行）を超える文字量」に限った。
