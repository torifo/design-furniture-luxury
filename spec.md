# VELA — design-furniture-luxury Spec

**Status:** Approved  
**Author:** torifo  
**Created:** 2026-05-19  
**Updated:** 2026-05-19

---

## 1. Overview

### Problem Statement
ラグジュアリー家具の購買層（40〜60代、高所得）が訪れる店舗サイトは「カタログ的に商品を並べる」か「ミニマルすぎて素材の価値が伝わらない」かに分かれており、美術館のように一点一点を丁寧に見せる体験を提供するサイトが少ない。

### Goal
「VELA」という架空のラグジュアリー家具ブランドのランディングページを実装し、Chapter形式（製品1点＝1画面）という構造で「急がずに選ぶ」購買体験を設計する。

### Non-Goals
- カート・決済機能
- CMS連携
- ローダー・マーキー・grain overlay・カスタムカーソル（HVILEとの差別化）

### Background
- VELAは架空ブランド。実在のブランド・商品ではない
- `design-furniture-luxury` リポジトリ予定
- HVILEとの比較：同じ家具カテゴリでペルソナ・構造・美学がどれだけ変わるかを検証

---

## 2. User Stories

| ID | Persona | Want to | So that |
|----|---------|---------|---------|
| US-01 | ラグジュアリー層 (40–60代) | 一度に1製品だけを見たい | 比較ではなく「この椅子が自分に必要か」を深く考えられる |
| US-02 | 同上 | 素材・寸法・製作期間を一画面で確認したい | カタログを別途見る必要がない |
| US-03 | 同上 | 問い合わせを気軽にできる形式で送りたい | 購入意思が固まった瞬間にアクションを取れる |
| US-04 | 同上 | どのデバイスでも格調高い体験を得たい | PCでもモバイルでもブランドへの信頼が維持される |

### Acceptance Criteria (EARS notation)

**US-01: Chapter形式スクロール**
- WHEN ページをスクロールした THEN 各製品セクションが最低100svhの高さを持ち、1画面に1製品が収まる
- WHEN 右サイドナビのドットをクリックした THEN 対応するChapterへスムーズスクロールする
- WHEN 各Chapterが50%以上ビューポートに入った THEN サイドナビのアクティブドットが切り替わる

**US-02: 製品スペック表示**
- WHEN Chapterが表示された THEN 素材・仕上げ・サイズ・リードタイムの4項目が2×2グリッドで表示される
- WHEN 製品画像にホバーした THEN scale 1.03のズームが1.2s easeで実行される

**US-03: Enquireフォーム**
- WHEN フォームを送信した THEN バリデーションが実行され（名前・メール必須）成功メッセージが表示される

**US-04: モバイル対応**
- WHEN 375px幅で閲覧した THEN Chapter画像とテキストが縦積みになり、サイドナビは非表示になる

---

## 3. Functional Requirements

| ID | Requirement | Priority | Notes |
|----|-------------|----------|-------|
| FR-01 | イントロ画面：中央大型ブランド名 + フェードイン | P0 | ローダーなし。フェードオンリー |
| FR-02 | 右サイドナビ（縦型ドット、アクティブ時に縦棒に変形） | P0 | PCのみ |
| FR-03 | Chapter形式製品セクション（min-height 100svh、画像60%/テキスト40%交互） | P0 | 3製品分 |
| FR-04 | 製品スペック2×2グリッド | P0 | 素材・仕上げ・サイズ・リードタイム |
| FR-05 | Enquire CTAボタン（各Chapter） | P0 | ページ内スクロール→フォームへ |
| FR-06 | ブランド引用セクション（全画面ダーク背景、中央イタリック） | P1 | |
| FR-07 | ストーリーセクション（2段組テキスト、max-width 640px中央） | P1 | |
| FR-08 | デュオ画像セクション（素材+職人、2分割） | P1 | |
| FR-09 | Enquireフォーム（名前・メール・興味のある製品） | P0 | |
| FR-10 | スクロールリビール（opacity + translateY、1s ease） | P1 | |
| FR-11 | モバイル対応 | P0 | 375px基準 |

---

## 4. Architecture

### Page Structure

```
index.html
├── nav.side-nav          # 右固定ドットナビ（PC）
├── nav#topNav            # 上部ナビ（ロゴ左・リンク右）
├── section.intro         # イントロ（100svh、中央タイポ）
├── section.chapter       # Chapter 01（60/40分割）
├── section.chapter.reverse # Chapter 02（40/60分割）
├── section.chapter       # Chapter 03
├── section.quote-section # ダーク引用（100svh）
├── section.story-section # ブランドストーリー（2段組）
├── div.duo-section       # 2分割画像（素材・職人）
├── section.enquire-section # Enquireフォーム
└── footer                # 3要素1行（ロゴ・コピーライト・リンク）
```

### Component Responsibilities

| Component | Responsibility |
|-----------|---------------|
| side-nav | ページ位置の可視化。ChapterのIntersectionObserverで更新 |
| .chapter | 1製品1画面。画像とスペック情報の並置 |
| .quote-section | ダーク反転でリズムを作る |
| .enquire-section | 受注制作のための問い合わせ起点 |

### Key Design Decisions

| Decision | Chosen | Rationale | Rejected alternatives |
|----------|--------|-----------|----------------------|
| レイアウト | Chapter（1製品1画面） | 「比較」ではなく「対話」させる体験 | 商品グリッド（カタログ的すぎる） |
| ローダー | なし | 即座に内容へ。待機は体験を損なう | あり（ARCH/HVILEと被る） |
| マーキー | なし | 急かす印象を与える | あり（ラグジュアリーに合わない） |
| grain/cursor | なし | 最小限の手数でプレミアム感を出す | あり（装飾過多） |
| ナビ | サイド縦型ドット | 読書のしおり的体験。画面を邪魔しない | 上部水平ページナビ |
| CTA | アウトラインボタン（hover反転） | 押し売りしない品格 | 塗りつぶし（攻撃的） |

---

## 5. Design System

### Color Palette
```css
--bg:     #FAFAF8;   /* ニュートラルウォームホワイト */
--fg:     #141210;   /* リッチブラック */
--muted:  #89817A;   /* ウォームグレー */
--border: #E5DED5;   /* サトルライン */
--gold:   #B8945A;   /* Chapter番号・CTA accent */
```

### Typography
```css
--font-serif: 'Playfair Display', Georgia, serif;
--font-sans:  'Jost', sans-serif;
```
- Google Fonts: `Playfair Display:ital,wght@0,400;0,500;0,700;1,400;1,500` + `Jost:wght@300;400;500`

### Motion
```css
--ease: cubic-bezier(0.4, 0, 0.2, 1);
/* image hover: scale 1.03, 1.2s */
/* reveal: opacity + translateY(16px), 1s ease */
/* chapter IntersectionObserver: threshold 0.4 */
```

---

## 9. Testing Strategy (Visual QA)

| Layer | Scenarios |
|-------|-----------|
| Desktop (1280px) | サイドナビ表示・Chapter 60/40切り替え・hover zoom |
| Mobile (375px) | サイドナビ非表示・縦積み・フォーム操作 |
| Enquireフォーム | バリデーション動作・送信成功メッセージ |
| IntersectionObserver | Chapter切り替え時のドットアクティブ化 |

---

## 10. Implementation Notes

- `min-height: 100svh` を使用（モバイルアドレスバー対応）
- `.chapter` の画像側に `overflow: hidden` + `position: relative`、`img` に `height: 100%; object-fit: cover`
- `.chapter.reverse` は `grid-template-columns: 40% 60%` かつ画像側の `order` を2に
- サイドナビのdotは `height: 4px` → active時 `height: 22px; border-radius: 2px`
- IntersectionObserver: `threshold: 0.4` で Chapter検知
- フォームバリデーションはHTML5 `required` 属性 + JS `.checkValidity()`
