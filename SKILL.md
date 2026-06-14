---
name: design-furniture-luxury
description: "furniture brand landing-page design study — 'luxury' theme/persona (pure HTML/CSS/JS, no build). Use when designing a 'luxury'-style furniture brand site aesthetic. Furniture for the Discerning Eye. furniture brandの「luxury」テーマLPのデザイン参照スキル。"
---

# design-furniture-luxury

A landing-page **design study** for a fictional **luxury**-theme furniture brand (pure HTML + CSS + vanilla JS, no build, GitHub-Pages ready). Use this as a **style / design-system reference** when building a similar aesthetic.

架空の「luxury」テーマのfurniture brand LP デザイン研究。同種の世界観を作るときの**スタイル／デザインシステム参照**として使う。

## When to use / 使いどころ
- **EN:** designing a 'luxury'-style furniture brand site — match its palette, typography and layout discipline.
- **JP:** 「luxury」系のfurniture brandサイトを設計するとき。配色・タイポ・レイアウト規律を流用。

## Bundled assets / 同梱アセット
This skill folder is the reference implementation — start from these files:
- `index.html` — full page markup
- `style.css` — design tokens (CSS custom properties) + layout
- `script.js` — vanilla JS (if present)
- `README.md` — full bilingual doc, brand context and series links

## Design reference / デザイン参照
_Lifted from the repo README — see README.md for the complete, bilingual version._

### Overview
**furniture design research series** の「ラグジュアリー」ペルソナ作品。

ラグジュアリー家具の購買層（40〜60代、高所得）が求める「比較ではなく対話」という体験を、Chapter形式（製品1点 = 1全画面）で実現する。美術館のように、一点一点を急がずに見せる設計。

---

### Brand
| | |
|--|--|
| **Brand** | VELA |
| **Tagline** | Furniture for the Discerning Eye |
| **Aesthetic** | ラグジュアリー・アトリエ × ミュージアム体験 |
| **Target Persona** | 40–60代、高所得、家具を一生ものの投資として選ぶ |
| **Color** | Warm White `#FAFAF8` + Gold `#B8945A` |
| **Display Font** | Playfair Display |
| **Body Font** | Jost |

---

### Design Approach
従来の家具ECが採用する「商品グリッド」を一切使わない。代わりに：

- **Chapter形式**: 製品3点がそれぞれ `min-height: 100svh` を占有
- **60/40 split**: 画像とテキストが等価に並ぶ。見開き雑誌の参照
- **Side chapter nav**: 右固定の縦型ドットナビ。読書のしおり的UX
- **Enquire CTA**: カートではなく問い合わせ。受注制作ブランドのフロー

**排除したUI要素**: ローダー・マーキー・grain overlay・カスタムカーソル・featurestrip

---

## Tech / 技術
- Vanilla HTML / CSS / JS — single file (`index.html`)
- Google Fonts: [Playfair Display](https://fonts.google.com/specimen/Playfair+Display), [Jost](https://fonts.google.com/specimen/Jost)
- ビルドツール不要

## How to apply / 適用方法
1. Reuse `style.css` custom properties (color / type / spacing tokens) as the design-system base.
2. Copy `index.html` layout as the starting structure, then swap brand name and content.
3. Keep the palette, font pairing and layout discipline described above.

---
> The brand is fictional (design study) — replace all brand/content. Full context: see **`README.md`**.
