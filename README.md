# もしもの防災会議 〜みんなでそなえる〜
防災士が開発した学校教育・地域防災学習向けの、無料で使える防災学習Webアプリです。
地図と組み合わせて、自分の地域の災害リスクを「自分ごと」として学べます。
PC（Windows・Mac）やスマフォやタブレットで利用可能です。（できるだけ画面が大きいものが推奨）

## 🌐 公開サイト

**▶ [もしもの防災会議を開く](https://tagmasa.github.io/bousai-meeting/)**

---

## 📖 概要

「もしもの防災会議」は、災害時の判断力を養うことを目的とした学習用Webアプリです。
地図を見ながら自分の地域の危険箇所を確認し、シミュレーション形式の問題に答えることで、実践的な防災知識を身につけられます。

### 主な特徴

- 🌏 **地図連携学習**：OpenStreetMap・地理院地図・3D地図など複数の地図を切り替え可能
- 📜 **8つの学習コース**：地震・津波・洪水・土砂崩れ・火災・地域編・避難所運営編・ボランティア編
- 📝 **A3ワークシート対応**：印刷して書き込みながら学べる
- 🏆 **修了証発行機能**：ブラウザ上で氏名入りの修了証を表示・印刷
- 📱 **マルチデバイス対応**：PC・タブレット・スマートフォン
- 🔒 **個人情報をサーバーに送信しない**：すべてブラウザ内で完結

---

## 🎯 想定される利用シーン

- 小学校・中学校・高校の防災教育の授業
- 地域の防災訓練・防災講座
- 自治体の防災セミナー
- 家庭での親子防災学習
- 防災士・防災ボランティアの研修

---

## 🚀 使い方

### 1. サイトを開く

公開URL（`https://tagmasa.github.io/bousai-meeting/`）にアクセスします。

### 2. 初期設定

初期設定画面で以下を入力します。

- 地図上で開始地点（中心地）を選択
- 想定最大浸水深（任意）
- お住まいの市町村名・避難所名・河川名・津波避難ビル・防災ラジオ局
- Cesium ion アクセストークン（3D地図機能を使う場合のみ必要・無料で取得と利用ができます）

### 3. 学習開始

「地図を開始する」ボタンを押すと、左側に地図、右側に学習コースが表示されます。
スマフォなど小さい画面の場合は切り替え表示されます。

### 4. ワークシート（地域編）

「地域編」を選択した場合は、別タブでワークシートを開いてA3サイズで印刷し、地図を見ながら書き込んで学習を進めます。

---

## 🌍 3D地図機能のご利用について

3D地図機能（Cesium 3D / Cesium(Google)）をご利用いただくには、利用者ご自身による Cesium ion の無料アカウント登録が必要です。

### トークン取得方法

1. https://ion.cesium.com/signup から無料アカウントを作成
2. https://ion.cesium.com/tokens からアクセストークンを取得
3. 「もしもの防災会議」の初期設定画面に貼り付け

> 💡 トークンを入力しなくても、3D地図以外のすべての機能（OpenStreetMap・地理院地図・防災学習コンテンツ・ワークシート等）は無料でご利用いただけます。

---

## 🔧 技術構成

純粋な静的HTMLサイト（HTML + CSS + JavaScript）として構成されています。サーバー側の処理は一切なく、Webブラウザ上で完結します。

| 構成要素 | 用途 |
|---|---|
| HTML / CSS / JavaScript | アプリ本体（フレームワーク非依存） |
| [Leaflet](https://leafletjs.com/) | 地図ピッカー（初期設定用） |
| [CesiumJS](https://cesium.com/platform/cesiumjs/) | 3D地図表示・津波シミュレーション |
| [Cesium ion](https://cesium.com/platform/cesium-ion/) | 3D地形・建物データ（利用者各自取得） |
| [OpenStreetMap](https://www.openstreetmap.org/) | ベース地図タイル |
| [国土地理院](https://maps.gsi.go.jp/) | 地形・土地分類・空中写真 |

---

## 📂 ファイル構成

```
bousai-meeting/
├── index.html                 # メインページ（地図連携画面・親ウィンドウ）
├── bousai-meeting.html        # 防災学習コンテンツ本体（iframe で読み込まれる）
├── bousai_worksheet_A3.html   # A3印刷用ワークシート
└── README.md                  # このファイル
```

---

## 💻 ローカル環境での動作確認

ローカルでテストする際は、**必ずHTTPサーバー経由で開いてください**。
`file://` プロトコルで直接開いた場合、Cesium の3D地図やWebWorkerが正しく動作しません。

> 💡 ローカル（サーバーやインターネットを用意できない・したくない場合）は3Dなどのマップは正しく動作しませんが、他の機能は利用できます。

### 開発推奨方法（VS Code 利用者）

1. [VS Code](https://code.visualstudio.com/) をインストール
2. 拡張機能「**Live Server**」をインストール
3. プロジェクトフォルダを VS Code で開く
4. `index.html` を右クリック → 「Open with Live Server」

### 開発推奨方法（Python 利用者）

```bash
cd bousai-meeting
python -m http.server 8000
```

ブラウザで http://localhost:8000 を開く。

### 開発推奨方法（Node.js 利用者）

```bash
cd bousai-meeting
npx serve
```

---

## 📜 ライセンス

本コンテンツは **クリエイティブ・コモンズ 表示-非営利-継承 4.0 国際 (CC BY-NC-SA 4.0)** でライセンスされています。

[![License: CC BY-NC-SA 4.0](https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.ja)

### 許可されること

- ✅ **共有** — どのような媒体・形式でも資料を複製、再配布できます
- ✅ **翻案** — 資料を変更したり、加工したりできます
- ✅ **教育目的での利用** — 学校・自治体・NPO等での非営利な教育利用

### 条件

- 📋 **表示（BY）** — 適切なクレジットを表示し、ライセンスへのリンクを提供してください
- 🚫 **非営利（NC）** — 営利目的での利用はできません
- 🔄 **継承（SA）** — 改変した場合は、同じライセンスで配布してください

詳細：https://creativecommons.org/licenses/by-nc-sa/4.0/deed.ja

---

## 🙏 出典・クレジット

本アプリは以下のオープンデータ・ライブラリを利用させていただいています。

- 地図データ © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors
- [国土地理院](https://maps.gsi.go.jp/development/ichiran.html) 地理院タイル
- [Cesium ion](https://cesium.com/) by Cesium GS, Inc.
- [Leaflet](https://leafletjs.com/) by Volodymyr Agafonkin

本アプリから以下のサイトへのリンクを設定させていただいています。
- [日本全国AEDマップ](https://aedm.jp/) －全国のAED設置場所を地図で共有－
- [国土交通省](https://disaportal.gsi.go.jp/hazardmap/maps/index.html) 国土交通省 - 重ねるハザードマップ

---

## 🚨 免責事項

本コンテンツは**防災学習を目的とした参考情報**です。実際の災害時には、必ず以下の公的機関の最新情報に従って行動してください。

- 気象庁：https://www.jma.go.jp/
- 内閣府防災情報：https://www.bousai.go.jp/
- お住まいの自治体・消防・警察

本コンテンツの内容に起因するいかなる損害についても、作者は責任を負いません。

---

## 💬 ご意見・改善提案

不具合の報告や改善のご提案は、GitHub の [Issues](https://github.com/tagmasa/bousai-meeting/issues) からお寄せください。

教育や防災の現場でご利用いただいた感想やフィードバックも歓迎します。

---

## 📅 更新履歴

- **2026年4月** — 公開版リリース
  - メインタイトルを「もしもの防災会議 〜みんなでそなえる〜」に変更
  - Cesium ion トークンを利用者各自取得方式に変更
  - セキュリティ強化（XSS対策・SRI追加・iframe sandbox 等）

---

## 📝 著作権

© 2026 田口雅章 — Released under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.ja)
