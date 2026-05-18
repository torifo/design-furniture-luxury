# VELA Design Learnings

## 目的

ラグジュアリー家具ペルソナ（40–60代、富裕層）は「比較」ではなく「対話」を求める。VELAでは、1製品1章（Chapter形式）という構造によって「急がずに選ぶ」体験を設計した。

VELAは架空ブランドであり、実在の店舗・商品ではない。

---

## このペルソナで捨てたもの

| 捨てたもの | 理由 |
|-----------|------|
| ローダー | 待機はラグジュアリー体験を損なう |
| マーキー | 急かす印象を与える。品格に反する |
| grain overlay | 装飾を最小化することでプレミアム感を出す |
| カスタムカーソル | HVILEとの差別化。カーソルは無言のサービスが担う |
| 商品グリッド | 並列比較より一点集中。美術館のような体験を優先 |
| features strip | スペックは各Chapterに内包。別セクションとして切り出さない |

---

## レイアウト

```
イントロ（100svh）→ Chapter 01（60/40）→ Chapter 02（40/60）→ Chapter 03（60/40）
→ 引用（100svh・ダーク）→ ストーリー（2段組）→ デュオ画像 → Enquireフォーム
```

`grid-template-columns: 60% 40%` の交互配置が「雑誌見開き」感を作る。`.chapter.reverse` で向きを反転させることで、単調な反復を防ぎながらリズムを維持する。

---

## CSS

主要な判断:

```css
/* Chapter単位の全画面 */
.chapter {
  min-height: 100svh;   /* svhでモバイルアドレスバー対応 */
  display: grid;
  grid-template-columns: 60% 40%;
  border-top: 1px solid var(--border);  /* 唯一の区切り */
}

/* Chapter番号はgold、製品名はセリフ */
.chapter-num  { color: var(--gold); letter-spacing: 0.4em; }
.chapter-name { font-family: var(--font-serif); font-weight: 400; font-size: clamp(2.2rem, 3.5vw, 4rem); }

/* CTAはアウトライン。hover反転で品格を維持しながら行動を促す */
.chapter-cta {
  border: 1px solid var(--border);
  transition: background .3s, color .3s, border-color .3s;
}
.chapter-cta:hover { background: var(--fg); color: var(--bg); border-color: var(--fg); }
```

`1px solid var(--border)` がVELAの設計言語。線が多いほど区切りが強調され、ラグジュアリー感が薄れる。

---

## フォント

- Display: `Playfair Display weight 400 / italic` — 古典的な品格。ハイエンドの「時代を超える」感覚
- Body: `Jost weight 300/400` — Outfitより細く、Cormorant Garamondより現代的

Playfair DisplayはVELAの「章のタイトル」としてのみ使用。本文には入れない。それがセリフの希少価値を維持する。

---

## サイドナビ

```css
.side-dot { width: 4px; height: 4px; background: var(--border); border-radius: 50%; }
.side-dot.active { height: 22px; border-radius: 2px; background: var(--fg); }
```

「丸→縦棒」の変形が読書のしおり的なUXを作る。IntersectionObserver の `threshold: 0.4` で、Chapterが半分以上入った時点でアクティブ化。

---

## アニメーション

- フェードイン `opacity 0 → 1` のみ。`translateY` は使わない
- 画像hover: `scale(1.03)` を `1.2s ease`。即座に戻らない「重さ」を演出
- リビール: `transition: opacity 1s ease` —– シリーズ最長。急がないブランドの性格

---

## furniture シリーズとの対比

| 軸 | HVILE（nordic） | VELA（luxury） |
|----|----------------|----------------|
| 構造 | ヒーロー→グリッド→マーキー→ダーク→フッター | Chapter×3→引用→フォーム |
| 製品表示 | カードグリッド | 全画面Chapter |
| ローダー | あり | なし |
| マーキー | あり | なし |
| フォント | Cormorant Garamond | Playfair Display |
| アクセント | セージ #3A5537 | ゴールド #B8945A |
| grain | あり (0.025) | なし |
| カーソル | あり（ウォームドット） | なし |
