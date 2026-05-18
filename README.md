# VELA — design-furniture-luxury

> **架空ブランド注記**: VELAは本デザイン研究のために作成した架空ブランドです。実在のブランド・店舗・商品ではありません。

---

## Overview

**furniture design research series** の「ラグジュアリー」ペルソナ作品。

ラグジュアリー家具の購買層（40〜60代、高所得）が求める「比較ではなく対話」という体験を、Chapter形式（製品1点 = 1全画面）で実現する。美術館のように、一点一点を急がずに見せる設計。

---

## Brand

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

## Design Approach

従来の家具ECが採用する「商品グリッド」を一切使わない。代わりに：

- **Chapter形式**: 製品3点がそれぞれ `min-height: 100svh` を占有
- **60/40 split**: 画像とテキストが等価に並ぶ。見開き雑誌の参照
- **Side chapter nav**: 右固定の縦型ドットナビ。読書のしおり的UX
- **Enquire CTA**: カートではなく問い合わせ。受注制作ブランドのフロー

**排除したUI要素**: ローダー・マーキー・grain overlay・カスタムカーソル・featurestrip

---

## Tech

- Vanilla HTML / CSS / JS — single file (`index.html`)
- Google Fonts: [Playfair Display](https://fonts.google.com/specimen/Playfair+Display), [Jost](https://fonts.google.com/specimen/Jost)
- ビルドツール不要

## Local Development

```bash
open index.html
# または
python3 -m http.server 8080
```

---

## Series

このリポジトリは **furniture design research series** の一作です。

| Theme | Brand | Aesthetic | Persona |
|-------|-------|-----------|---------|
| [nordic](../nordic/) | HVILE | 北欧オーガニック | 30–45代、素材重視の住まい手 |
| **luxury** | **VELA** | **ラグジュアリー・アトリエ** | **40–60代、ラグジュアリー層** |
| [artisan](../artisan/) | BURL | 職人工房・カタログ | 25–45代、クラフト志向 |
| [urban](../urban/) | BLOC | アーバン・グラフィック | 20–35代、都市生活者 |

同一カテゴリ（家具）でも、ペルソナが変われば構造・美学・UIパターンがどれだけ変わるかを探る研究です。
