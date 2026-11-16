# コード整理計画（棚卸し）— 2026-11-15

実サイトは変更していない。調査と文書化のみ。
調査材料：追加CSSバックアップ2種（custom-css-backup-20261112.txt／custom-css-backup-20261114-pre-p0a.txt）、design-refresh.md、posting-status.md、live-list-data.json、card-badges.json、および2026-11-15に curl で取得した公開ページ https://www.kpopliveinjapan.com/live-event/ のHTML（`<style id="wp-custom-css">` とページ内 script／style を抽出して解析）。

要点：削除・整理候補は**計6件**（追加CSSの無効ブロック2件、固定ページID63内の旧JS 3件＋旧CSS 1件）。いずれも「現行の表示は別の実装が担っている」ことを記録と実物で確認済み。

---

## ① 削除・整理候補

### 候補1：追加CSS 無効ブロックA「ライブ一覧カードタイトル修正」（初回試行）

- **場所**：カスタマイザー「追加CSS」。ライブ側 673〜692行目（2026-11-15取得のライブCSSで確認。バックアップ custom-css-backup-20261114-pre-p0a.txt でも同じ673〜692行目）
- **内容（全文）**：

```css
/* 2026-11-14 ライブ一覧カードタイトル修正 */
body.page-id-63 main a.p-postList__link .p-postList__title,
body.page-id-63 .p-postList__title {
  background: none !important;
  background-image: none !important;
  background-color: transparent !important;
  border: none !important;
  border-top: none !important;
  border-bottom: none !important;
  box-shadow: none !important;
}
body.page-id-63 main a.p-postList__link .p-postList__title::before,
body.page-id-63 main a.p-postList__link .p-postList__title::after,
body.page-id-63 .p-postList__title::before,
body.page-id-63 .p-postList__title::after {
  display: none !important;
  content: none !important;
  background: none !important;
  background-image: none !important;
}
```

- **なぜ不要**：design-refresh.md「2026-11-14 修正」に「同目的で先に試した2ブロック（「ライブ一覧カードタイトル修正」「（カード内h2追加）」）はセレクタ不一致で無効のまま追加CSS内に残存（無害。整理時はこの2ブロックのみ削除可）」と明記。本ブロックは `.p-postList__title` を対象にするが、実際に帯が当たっていたのはリンク内の h2 要素であり、セレクタが届いていない。同目的は有効ブロック「（帯の除去・再試行）」（②参照）が達成済み。
- **削除手順**：候補2と合わせて次項の一括削除で行う。
- **ロールバック**：削除前に保存するライブ全文バックアップ（実施手順参照）から、本ブロックを元の位置（「（帯の除去・再試行）」ブロックの直前）に再挿入する。

### 候補2：追加CSS 無効ブロックB「ライブ一覧カードタイトル修正（カード内h2追加）」

- **場所**：カスタマイザー「追加CSS」。ライブ側 693〜712行目（バックアップでも同位置）。直後の713行目は空行。
- **内容（全文）**：

```css
/* 2026-11-14 ライブ一覧カードタイトル修正（カード内h2追加） */
body.page-id-63 main a[href] h2,
body.page-id-63 main .post_content h2 {
  background: none !important;
  background-image: none !important;
  background-color: transparent !important;
  border: none !important;
  border-top: none !important;
  border-bottom: none !important;
  box-shadow: none !important;
}
body.page-id-63 main a[href] h2::before,
body.page-id-63 main a[href] h2::after,
body.page-id-63 main .post_content h2::before,
body.page-id-63 main .post_content h2::after {
  display: none !important;
  content: none !important;
  background: none !important;
  background-image: none !important;
}
```

- **なぜ不要**：候補1と同じく design-refresh.md で「セレクタ不一致で無効」と明記された試行ブロック。有効ブロックが後段で同内容を上書き済みのため、削除しても描画は変わらない。
- **削除手順（候補1・2共通）**：管理者でカスタマイザー→追加CSSを開き、コメント `/* 2026-11-14 ライブ一覧カードタイトル修正 */` から `（カード内h2追加）` ブロックの閉じ `}` まで（ライブ側673〜712行目相当、ついでに直後の空行713行目も）を選択して削除する。**行番号だけに頼らず、開始コメントと終了位置（次の有効ブロックのコメント `/* 2026-11-14 ライブ一覧カードタイトル修正（帯の除去・再試行） */` の直前まで）で範囲を確認すること。**直前にある「ヘッダーボタン修正（固定ヘッダーの上下位置）」ブロック（〜671行目）は現行なので巻き込まない。
- **ロールバック**：候補1と同じ（バックアップから2ブロックを再挿入）。

### 候補3：固定ページID63 旧JS「T」（公演未発表ラベルの旧実装）

- **場所**：固定ページID63（ライブ一覧）本文内のカスタムHTMLブロックのうち、`var T=[` で始まるスクリプト（約790字）。公開HTMLからはブロックの順序を確定できないため、実施時はコードエディタ内で `var T=` を検索して特定する。
- **内容（抜粋。取得したHTMLのまま）**：

```js
(function(){var T=['babymonster','i-dle','blackpink','treasure','zerobaseone','aespa','riize','seventeen','bts','exo','shinee','tvxq','twice','itzy','ive'];function add(){T.forEach(function(s){var L=document.querySelectorAll('a[href*"+s+'/"]); … e.className='live-tbd-label';e.textContent='公演未発表'; … }})(); 
```

- **なぜ不要**：①枠記事カードの「公演未発表」表示は、現行ではページ内 style の `figure::after`（②参照）が担っている。②posting-status.md に「固定ページID63内には表示に使われていない旧JS（T／U／TEST）…のデッドコードが残っている（未削除）」と明記。③取得したHTML上では引用符や綴りが壊れており（`'a[href*"+s+'/"]'`、`querySelector('im'g)`、`closeest`、`createEleement`、`ifgetComputedStyle` 等）、JavaScript として構文エラーで実行不能。
- **削除手順**：ID63をコードエディタで開き、当該 `<script>…</script>`（またはそれを含むカスタムHTMLブロック）ごと削除する。
- **ロールバック**：削除前に保存するID63本文のバックアップから当該ブロックを復元する。

### 候補4：固定ページID63 旧JS「U」（同・書き直し版）

- **場所**：ID63本文内、`var U=[` で始まるスクリプト（約570字）。
- **内容（全文）**：

```js
(function(){var U=['babymonster','i-dle','blackpink','treasure','zerobaseone','aespa','riize','seventeen','bts','exo','shinee','tvxq','twice','itzy','ive'];function a(){U.forEach(function(s){var q=document.querySelectorAll('a[href*="/'+s+'/"']');for(var i=0;i<q.length;i++){var g=q[i].querySelector('img');if(!g)continue;var w=g.closest('figure')||g.parentElement;if(!w||w.querySelector('.live-tbd-label'))continue;var e=document.createElement('span');e.className='live-tbd-label';e.textContent='公演未発表';w.appendChild(e)}})}a();setTimeout(a,800);setTimeout(a,2500)})();
```

- **なぜ不要**：候補3と同じ役割（枠15組への `.live-tbd-label` 付与）の書き直し版で、現行表示は `figure::after` が担う。posting-status.md でも「表示に使われていない旧JS」に含まれる。構文自体は正常なため実行はされ得るが、挿入される span は現行の ::after と同一位置・同一文言・同一見た目で重なるだけで、表示上の役割はない。
- **削除手順**：候補3と同様にブロックごと削除。**削除後はライブ一覧で枠カードの「公演未発表」が ::after で表示され続けていることを必ず目視確認する**（本候補は実行され得るため、候補3・5より確認を丁寧に）。
- **ロールバック**：候補3と同じ。

### 候補5：固定ページID63 テスト用JS「TEST-IVE」

- **場所**：ID63本文内、IVEカードへのラベル付けを行う即時実行スクリプト（約290字）。`'TEST-IVE'` の文字列で検索して特定する。
- **内容（全文）**：

```js
(function(){var l=document.querySelector('a[href*="/ive/"]');if(!l)return;var g=l.querySelector('img');if(!g)return;var w=g.closest('figure')||g.parentElement;if(!w)return;var e=document.createElement('span');e.className='live-tbd-label';e.textContent='TEST-IVE';w.appendChild(e);})();
```

- **なぜ不要**：文言どおりテスト用の残骸。posting-status.md の言う「TEST」に該当。現行の IVE カードの「公演未発表」表示は ::after が担っており、本スクリプトは表示に使われていない。
- **削除手順／ロールバック**：候補3と同じ。削除後は IVE カードの表示（「公演未発表」が ::after で出ていること）を確認する。

### 候補6：固定ページID63 `.live-tbd-label` 用 style ブロック

- **場所**：ID63本文内の `<style>` ブロック（約360字）。
- **内容（全文）**：

```css
.live-tbd-label{position:absolute;top:8px;left:8px;z-index:6;pointer-events:none;background:#6b7280;color:#fff;font-weight:700;font-size:12px;line-eight:1.4;padding:5px 10px;border-radius:999px;box-shadow:0 2px 8px rgba(0,0,0,.4);letter-spacing:.02em;white-space:nowrap;}
@media(max-width:600px){.live-tbd-label{font-size:11px;padding:4px 9px;top:6px;left:6px;}}
```

（`line-eight` は無効なプロパティ名で、もともと効いていない。）
- **なぜ不要**：参照するクラス `.live-tbd-label` を生成するのは候補3〜5の旧JSだけ。posting-status.md でも「.live-tbd-label 用CSSのデッドコード」と明記。
- **削除手順**：**必ず候補3〜5のJS削除と同時に行うこと。** JS が残っている間に本CSSだけ消すと、万一スクリプトが実行された際に無スタイルの span が残る。逆も同様で、セットで消す。
- **ロールバック**：候補3と同じ（ID63本文バックアップから復元）。

---

## ② 触ってはいけない現行コード

### 追加CSS（カスタマイザー）

| 対象 | 場所（ライブ行） | 理由 |
|---|---|---|
| `/* 2026-11-14 ライブ一覧カードタイトル修正（帯の除去・再試行） */` | 714〜733行目 | カードタイトル先頭文字欠けを実際に解消した**有効ブロック**。候補1・2と名前が酷似しているため誤削除に最注意 |
| `/* 2026-11-14 ヘッダーボタン修正 */` および `/* 2026-11-14 ヘッダーボタン修正（固定ヘッダーの上下位置） */` | 641行目〜／665〜671行目 | 固定ヘッダーのCTAボタンの現行修正。候補1の直前にあるため巻き込み注意 |
| `/* === 2026-11-14 デザインP0 A群 === */` 以降 | 734行目〜末尾 | ピルコントラスト補正・本文サイズ固定・prefers-reduced-motion の現行ブロック |
| 上記以外の既存ブロック全般 | 1〜640行目ほか | 本棚卸しの対象外（見出し補正系、ヒーロー高さ補正3＝スマホ36vh確定値、チェック修正1〜3、2026-11-12第2弾など、すべて現行） |

### 固定ページID63（ライブ一覧）

| 対象 | 内容 | 理由 |
|---|---|---|
| メインスクリプト（約7,100字） | `var DATA={…}`（50件）＋`var BADGE={…}`（27件）＋並び替え（開催日順／名前順）＋`.live-badge` 生成 | 一覧の心臓部。BADGE のピルは次スクリプトで除去されるが、**BADGEデータ自体は締切抽出の入力として現行必須**（ピルを出さず締切だけ出すのは2026-11-12に意図して決めた仕様）。ローカル正本 live-list-data.json（posts 50件／cardTitles 50件）・card-badges.json（27件）とキー一致を確認済み |
| LABELSスクリプト（約1,600字）＋ `.live-thumb-label` 用 style | サムネイル左上の「チケット発売中／先行受付中」ラベル（20件） | 現行表示。「受付中のみ」フィルタの判定（`.live-thumb-label` の有無）にも使われている |
| 締切抽出スクリプト（約2,200字） | `.live-badge` のピル文言から「締切 M/D」を抽出して `.live-deadline` を生成し `.live-badge` を除去、締切なしカードへの空の締切行挿入、「受付中のみ」トグルの追加、初期表示で開催日順を自動適用 | 現行。メインスクリプトと対で動作するため単独で触らない |
| CARDTITLESスクリプト（約2,900字） | `var CARDTITLES={…}`（50件）でカード見出し h2 を短縮タイトルに置換 | ルールAの現行実装。正本は live-list-data.json の cardTitles |
| ページ内 style 群 | `.live-sort`／`.live-badge` 系、`.live-deadline`／`.live-only` 系 | 現行の並び替えUI・締切表示のスタイル |
| `figure::after` の「公演未発表」style（約610字） | `.c-postThumb__figure{position:relative}` ＋枠15組の `a[href*=…] figure::after{content:'公演未発表';…}` | **枠カードの「公演未発表」表示の現行実装そのもの**。候補3〜6を消しても表示が維持される根拠。絶対に消さない |
| 並び替えボタン等のHTMLマークアップ | `.live-sort` のボタン群など | 上記スクリプトの操作対象 |

※参考（任意・今回の削除候補には入れない）：メインスクリプトの `.live-badge` 生成→締切抽出スクリプトでの除去は「ピルを作って捨てる」形だが、現行仕様どおりに動作している。締切だけを直接生成する形への書き換えは等価変換として可能だが、動作中のコードの書き換えリスクに見合わないため、触るなら別途検証付きで判断すること。

---

## 実施時の共通手順（将来実施する場合）

1. **事前バックアップ（必須）**：ライブの追加CSS全文と、ID63本文（コードエディタ表示の全文）を、それぞれ新規ファイルとして保存する。既存の custom-css-backup-20261114-pre-p0a.txt は P0 A群追記前の状態であり、現行ライブ（P0ブロックを含む）とは一致しないため、そのままではロールバックに使えない。
2. **削除の目印**：行番号は2026-11-15取得時点のライブCSSでバックアップと一致していたが、実施時は行番号ではなくコメント文字列・開始パターン（`var T=`、`var U=`、`'TEST-IVE'`、`.live-tbd-label`）で対象を特定する。
3. **削除後の確認**：ライブ一覧で 並び替え（開催日順／名前順）、「受付中のみ」、締切表示、サムネイル左上ラベル、枠カードの「公演未発表」、カードタイトルに帯が被っていないこと をPC／スマホ幅で目視確認。あわせてトップページと記事ページ（追加CSSの影響範囲）も確認する。
4. **ロールバック**：問題があれば、手順1のバックアップ全文をそのまま戻す（追加CSSはカスタマイザーへ貼り戻し、ID63は本文へ貼り戻し）。部分復旧は、削除したブロックを元の位置へ再挿入する。
