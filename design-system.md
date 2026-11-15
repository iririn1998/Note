# デザインシステムとは？（定義と構成要素のまとめ）

「デザインシステムとは何か」、そして単なるパーツ集やルールブックを超えて「**何があればデザインシステムといえるのか**」について、国内外の代表的な機関・企業の定義をもとにまとめたノートです。

---

## 1. デザインシステムとは？

一言でいうと、**「ブランドやプロダクトの一貫性を保ちながら、効率的かつスケーラブルにデザイン・開発を行うための『思想（原則）』『ルール（ガイドライン）』『再利用可能な部品（UI・コード）』『運用体制』の集合体（仕組み）」**です。

各機関・企業では以下のように定義されています。

* **デジタル庁の定義**
  > 「ブランドやコミュニケーションの価値観定義を指針化した**デザインプリンシプル**、情報アーキテクチャとインタラクションデザインに基づいた**コンポーネント定義**、アクセシビリティを含んだ規範となる**デザインガイドライン**といった、**デザインアセットの集合体**」
  * デザイナーやエンジニアだけでなく、企画・営業などあらゆる関係者が共通認識を持つための「バウンダリーオブジェクト（部門間の橋渡しをする共通指標）」として機能する仕組みと位置づけています。
  * **参照元**: [デザインシステムとは｜デジタル庁デザインシステムβ版](https://design.digital.go.jp/dads/guidance/design-system/)

* **Nielsen Norman Group (NN/g) の定義**
  > 「再利用可能なコンポーネントとパターンを用いて、大規模なデザインを管理するための完全な基準のセット（A complete set of standards intended to manage design at scale using reusable components and patterns）」
  * 車輪の再発明（重複作業）を減らし、チーム間の共通言語と視覚的一貫性を生み出す「唯一の情報源（Single Source of Truth）」と定義しています。
  * **参照元**: [Design Systems 101 - Nielsen Norman Group](https://www.nngroup.com/articles/design-systems-101/)

* **SmartHR / Ameba (サイバーエージェント) の定義**
  * **SmartHR**: 「誰もがSmartHRらしい表現をするための基準や素材をまとめたもの」「すべての人によりよい体験を届けるためのデザインシステム」
    * **参照元**: [SmartHR Design System](https://smarthr.design/)
  * **Ameba (Spindle)**: 「Amebaを作るすべての人が『Amebaらしさ』をつくるための約束事や、それを手助けするツールやガイドラインが揃った仕組み」
    * **参照元**: [Spindle (Ameba Design System)](https://spindle.ameba.design/)

---

## 2. 何があれば「デザインシステム」といえるのか？

「FigmaのUIパーツ集があるだけ」「ブランドカラーのPDFがあるだけ」では、厳密にはデザインシステムとは呼べません。
上記の定義を総合すると、**以下の5つの要素が揃い、デザインと実装（コード）が連動して継続運用されている状態**をもって「デザインシステム」といえます。

### ① デザイン原則（Design Principles）【Why：思想・判断基準】
* プロダクトやブランドが最も大切にする価値観や、「迷ったときにどう判断するか」の指針。
* **具体例**:
  * デジタル庁：「アクセシビリティファースト」
  * SmartHR：「ユーザーの時間は有限だ」「言葉からはじまるデザイン」
* **参照元**:
  * [デザイン原則 | SmartHR Design System](https://smarthr.design/products/principles/)
  * [原則 - Spindle](https://spindle.ameba.design/principles/)

### ② スタイルガイド / 基本要素（Foundations & Design Tokens）【What：視覚・言語の基礎】
* ブランドやUIの土台となる視覚的・言語的ルール。
* **含まれるもの**:
  * カラーパレット（ブランドカラー、UIセマンティックカラー）
  * タイポグラフィ（フォント、文字サイズ、行間）
  * 余白（スペーシング）、レイアウトグリッド、角丸、シャドウ
  * アイコン、イラストレーション、ロゴ規定
  * ライティングルール（トーン＆マナー、表記ゆれ防止、UIラベリング）
* **デザイントークン（Design Tokens）**: 色や余白などの値を `#0066CC` のような直接指定ではなく、`color-primary` のような共通変数（トークン）として定義し、デザインツール（Figma等）とコード（CSS/JS等）の双方で同期する仕組み。
* **参照元**:
  * [Design Systems vs. Style Guides - Nielsen Norman Group](https://www.nngroup.com/articles/design-systems-vs-style-guides/)
  * [デジタル庁デザインシステムβ版](https://design.digital.go.jp/)

### ③ コンポーネントライブラリ ＆ パターンライブラリ【What：再利用可能な部品と実装コード】
* **UIコンポーネントライブラリ**: ボタン、入力フォーム、モーダルなど再利用可能なUIパーツ群。
  * **重要ポイント**: Figmaなどの**デザインデータだけでなく、エンジニアがそのまま使える実装コード（React/Vueコンポーネント、HTML/CSSスニペット、Storybookなど）と1対1で紐づいていること**が不可欠です。
* **パターンライブラリ**: 個別のコンポーネントを組み合わせた「ページヘッダー」「検索結果一覧」「認証フォーム」などのUIグループや画面レイアウトのテンプレート。
* **参照元**: [Design Systems 101 - Nielsen Norman Group](https://www.nngroup.com/articles/design-systems-101/)

### ④ 利用ガイドライン・仕様ドキュメント【How：使い方の規範】
* パーツを「どう使うか」「いつ使うべきでないか」を明文化したドキュメント。
* **含まれるもの**:
  * コンポーネントの名称（デザイナーとエンジニアの共通言語）
  * 用途と文脈、良い例・悪い例（Do's and Don'ts）
  * 状態変化の仕様（Default / Hover / Focus / Disabled / Error など）
  * アクセシビリティ要件（WCAG基準のコントラスト比、キーボード操作、スクリーンリーダー対応など）
* **参照元**:
  * [Design Systems 101 - Nielsen Norman Group](https://www.nngroup.com/articles/design-systems-101/)
  * [デザインシステムとは｜デジタル庁デザインシステムβ版](https://design.digital.go.jp/dads/guidance/design-system/)

### ⑤ 運用体制・ガバナンス（People & Process）【Who：育てる仕組み】
* Nielsen Norman Groupは、デザインシステムを成立させる2大要素として**「① デザインリポジトリ（上記①〜④の資産）」**と**「② それを管理・運用する人々（チーム）」**を挙げています。
* デザインシステムは一度作って終わりではなく、プロダクトの変化や技術の進化に合わせて継続的にアップデートされる「リビングスタンダード（生きた基準）」である必要があります。
* **参照元**: [Design Systems 101 - Nielsen Norman Group](https://www.nngroup.com/articles/design-systems-101/)

---

## 3. よく混同される用語との違い（どこからがデザインシステムか？）

Nielsen Norman Groupは、デザインシステムと他の用語を**「親（デザインシステム）と子（構成要素）」の包含関係**として整理しています。

| 用語 | 役割・スコープ | これ単体でデザインシステムといえるか？ |
| :--- | :--- | :--- |
| **スタイルガイド**<br>(Style Guide) | 色、フォント、ロゴ、文章のトーン＆マナーなど、**特定の側面の見た目や表現ルールをまとめた静的なドキュメント**。 | **× いえない**（デザインシステムを構成する「子」要素の1つ） |
| **UIキット / デザインデータ**<br>(UI Kit) | Figmaなどのデザインツール上で、パーツやスタイルを再利用できるようにまとめた**デザイナー向けのファイル**。 | **× いえない**（実装コードや原則・運用ルールが欠けているため） |
| **コンポーネントライブラリ**<br>(Component Library) | 再利用可能なUIパーツの**デザイン・実装コード・仕様書をまとめた部品箱**（Storybookなど）。 | **△ 惜しいが単体では不十分**（部品箱だけでなく、上位の「デザイン原則」や「スタイルガイド」「パターン」と統合されて初めてデザインシステムになる） |
| **デザインシステム**<br>(Design System) | **原則（思想）＋ スタイルガイド ＋ コンポーネント/パターン（デザイン＆コード）＋ ガイドライン ＋ 運用体制**をすべて統合した全体（親）。 | **◎ デザインシステムといえる** |

* **参照元**: [Design Systems vs. Style Guides - Nielsen Norman Group](https://www.nngroup.com/articles/design-systems-vs-style-guides/)

---

## 4. チェックリスト：自分たちのものは「デザインシステム」か？

以下を満たしていれば、胸を張って「デザインシステム」と呼ぶことができます。

- [ ] **Why（原則）**: 意思決定の基準となる「デザイン原則」が言語化されているか？
- [ ] **Foundation（基礎）**: 色・文字・余白などの基本スタイル（またはデザイントークン）が定義されているか？
- [ ] **Design & Code（部品の同期）**: デザイナーが使うUIパーツ（Figma等）と、エンジニアが使うUIコンポーネント（コード）が同じ名前・仕様で連携しているか？
- [ ] **Guidelines（規範）**: 各パーツの「使い分けルール」「アクセシビリティ基準」「状態変化」がドキュメント化され、誰でも参照できる場所（専用サイトやWiki等）にあるか？
- [ ] **Governance（運用）**: 形骸化しないよう、更新・改善し続けるためのルールや担当体制があるか？

---

## 5. 参照元URL一覧

* **デジタル庁デザインシステムβ版「デザインシステムとは」**: https://design.digital.go.jp/dads/guidance/design-system/
* **デジタル庁デザインシステムβ版 トップページ**: https://design.digital.go.jp/
* **Nielsen Norman Group "Design Systems 101"**: https://www.nngroup.com/articles/design-systems-101/
* **Nielsen Norman Group "Design Systems vs. Style Guides"**: https://www.nngroup.com/articles/design-systems-vs-style-guides/
* **SmartHR Design System**: https://smarthr.design/
* **SmartHR Design System「デザイン原則」**: https://smarthr.design/products/principles/
* **Spindle (Ameba Design System)**: https://spindle.ameba.design/
