# pm-lp — PM特化 転職LP（求職者向け）

- 公開URL: https://pm.agent-best.net/ （GitHub Pages・HTTPS強制）
- 構成: `index.html` 1ファイル完結。CSS/JSはインライン、**外部CDNは読み込まない**。`CNAME` あり。

## ターゲットと訴求（変えるときは理由を確認する）

本命は **「大手SIer・大手コンサルのPM」**。年収・安定はあるが「事業を背負う裁量（オーナーシップ）」がない層。

- ヒーロー「年収は、下げない。／裁量は、上げる。／場所は、選ぶ。」
- 論点は「裁量の有無」ではなく **「"提案する裁量"と"事業を背負う裁量"の違い」**。大手にも裁量はあると認めた上で精度を上げている。「大手には裁量がない」に単純化しない。
- 転職先は上場グロース企業〜**超成長スタートアップ**。表記は「SU」ではなく「スタートアップ」。
- 匿名アーキタイプ事例＝経営管理／ERP系、行政GovTech予算編成、フィンテック上場、BtoB SaaS上場。
- 根拠データ: 日経「NEXTユニコーン調査」（有力スタートアップ平均年収 2021年度650万→2025年度777万）。

## ⚠ 対外表記ルール（最重要・2026-08-02確定）

- **サイト名・リンク表記は「PM特化」で統一。PMO は書かない。PjM・PdM も併記しない。**
  `<title>`・meta description・ヒーローラベルからPMOは削除済み。戻さないこと。
- **PMOは対象外**。対応領域の記述も「大規模プロジェクトの推進・全体統括」に変更済み。
- ただし**本文の PjM／PdM 2軸構成**（「PjM・PdM、どちらのキャリアにも。」の章・事例・FAQ）は**維持**する。
  ＝ ラベルはPMに寄せ、中身は両対応、が正しい状態。
- 本文中の「**フリーランスPMO**」への言及2か所は、当社の対応領域ではなく**市場・読み手の状況説明**なので意図的に残してある。消すと論旨が崩れる。

## 数字の扱い

ページ内のサービス指標と利用者の声は**実値の確定待ちの項目がある**。差し替える話が出たら、勝手に数字を作らず必ず本人に確認する。新しい数字を足すときも一次ソースか実測値のみ。

---

## 求職者向けLP 共通ルール

- **CTA**（「話を聞いてみる」「無料で相談する」「面談予約」）のリンクは `https://calendly.com/r_matsuoka` 固定。`target="_blank" rel="noopener"` で開く。
- **GA4 測定ID** `G-1XXMP8Y1B4`（全サブドメイン共通プロパティ）。
- **ダークモード対応**（`prefers-color-scheme` ＋ `[data-theme]` の両対応）を壊さない。
- 事例・行き先は**社名・ロゴを出さない匿名アーキタイプ**で書く。
- 掲載する数字は**必ず一次ソース付き**。出典が取れない数字は載せず、空欄のままにする。架空の利用者の声や根拠のない自社指標（「年収アップ率○%」「独占求人多数」等）は入れない。
- 棒グラフの `.track` / `.fill` を `<span>` で書くと**描画されない**（inline要素なので width/height が効かない）。`display:block` が必要。pm-lp由来の既知バグで、他LPにも伝播している可能性が高い。
- ローカルプレビューは `file://` だと確認できないので、簡易HTTPサーバー（node）を立てて `http://localhost:<port>/` で見る。

## 相互リンク（求職者向け8本）

| サブドメイン | 内容 | リポジトリ |
|---|---|---|
| pm | PM特化 転職 | agentbest/pm-lp |
| eng | エンジニア→コンサル転職 | agentbest/engineer-consultant |
| ma | 未経験からM&A | agentbest/ma-lp |
| consul | 未経験からコンサル | agentbest/consultant-lp |
| engineer | 未経験からエンジニア | agentbest/engineer-lp |
| embedded | IoT・組込みエンジニア | agentbest/embedded-lp |
| consultingcareerchange50 | ファーム出身者の次のキャリア（50代） | agentbest/consultingcareerchange50 |
| student | 学生キャリア支援 | agentbest/student-career |

フッターに `.ft-links` を再利用した2つ目のnav（`ft-sites-links`）で自分以外の7本を並べる。**新しいLPを足したら既存全部＋コーポレート `agentbest/agentbest-lp` の `src/components/Header.astro` の `specialSites['求職者の方へ']` も更新する。片方向にしない。**

⚠ 一括置換の罠: アンカーに `ft-sites-links` の文字列だけを使うと `<style>` 内のCSS定義にマッチして**ヘッダーnavに誤挿入される**（student-careerで実際にやらかした）。`<nav class="ft-links ft-sites-links">` のようにタグごと指定すること。

採用企業向け（B2B）4本（scout / green / infra / scoutdaikou_offerbox）は読み手が違うので、この相互リンクには**意図的に含めない**。

## push のルール

- ローカルで動作確認（ブラウザ表示・構文チェック）を済ませた変更は、**確認を取らずに commit & push してよい**。コミットメッセージは日本語。**push後は必ず何を変えたか報告する**（無言でpushしない）。
- **以下に触れるときは必ず止まって事前確認する**:
  1. ドメイン・DNS・CNAME（DNSは**Squarespace Domains**管理・松岡さんの手作業）
  2. 個人情報・フォーム・認証
  3. 費用が発生する変更
  4. 既存ページ・データの削除
  5. 複数リポジトリへの一括変更（相互リンク更新など）
- Publicリポジトリ。push前にトークン・APIキーの混入をgrepで確認する。
- `main` への push = **即本番公開**。
