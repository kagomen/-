## 🐌 概要

- 月毎に、日々の学習内容を簡単に記録しています

  - [2024 年 4 月分](https://github.com/kagomen/TIL/blob/main/2024-04.md)
  - [2024 年 5 月分](https://github.com/kagomen/TIL/blob/main/2024-05.md)
  - [2024 年 6 月分](https://github.com/kagomen/TIL/blob/main/2024-06.md)
  - [2024 年 7 月分](https://github.com/kagomen/TIL/blob/main/2024-07.md)
  - [2024 年 8 月分](https://github.com/kagomen/TIL/blob/main/2024-08.md)
  - [2024 年 9 月分](https://github.com/kagomen/TIL/blob/main/2024-09.md)
  - [2024 年 10 月分](https://github.com/kagomen/TIL/blob/main/2024-10.md)
  - [2024 年 11 月分](https://github.com/kagomen/TIL/blob/main/2024-11.md)
  - [2024 年 12 月分](https://github.com/kagomen/TIL/blob/main/2024-12.md)

---

## 🏃‍♀️ これまでのまとめ

## 2023 年 12 月

- プログラミング学習開始 💻
- ドットインストールで HTML, CSS, JavaScript, PHP の基礎を学習

## 2024 年 1 月

- ドットインストール「JavaScript でミニアプリをつくろう」を見ながらアプリを制作
  - CSS 部分のみオリジナル
    - [ビンゴシートアプリ](https://kagomen.github.io/BingoSheet/)
    - [カレンダーアプリ](https://kagomen.github.io/Calendar/)
    - [ストップウォッチアプリ](https://kagomen.github.io/Stopwatch/)
    - [ToDo アプリ](https://kagomen.github.io/TodoApp-js/)
- ドットインストールで React と Laravel の基礎を学習

## 2 月

- Astro と microCMS で[個人ブログ](https://kagome.pages.dev/)を制作
  - 運用せず。[Scrapbox](https://scrapbox.io/kagomen/)を継続利用中
- Udemy で React の基礎を学習

## 3 月

- 【継続】Udemy で React の基礎を学習
- 共同プロジェクト [First Contributions JA](https://github.com/kagomen/first-contributions-ja.github.io) に参加
  - チーム開発における GitHub の使い方について学ぶ
    - イシューのたて方
    - プルリク・コードレビューの方法
    - Discussions や Projects の使い方
    - テンプレートの作成方法
    - セマンティックバージョニングについて
  - 考えたことの言語化・伝え方・チームでの立ち振る舞いについて模索
  - アイデア出しは FigJam を使用した

## 4 月

- 【継続】共同プロジェクト [First Contributions JA](https://github.com/kagomen/first-contributions-ja.github.io) に参加
  - [Version1.0.0](https://github.com/first-contributions-ja/first-contributions-ja.github.io/releases/tag/v1.0.0)リリース
- JavaScript で簡単なゲームアプリを 1 から作る
  - [10 秒ストップウォッチゲーム](https://kagomen.github.io/10second-game/)
  - [15 パズルゲーム](https://kagomen.github.io/15puzzle/)

## 5 月

- JavaScript でゲームアプリを 1 から作る
  - [倉庫番ゲーム](https://kagomen.github.io/sokoban/)
    - ビット演算について学ぶ
- モダン JavaScript とその周辺技術を調査
  - Webpack, Babel, npm, Vite, TypeScript などの役割や設定ファイルの記述方法について
- React での Web API の扱い方を簡単なアプリを作りながら学ぶ
  - [Pixabay API を使った画像検索アプリ](https://pixabay-api-app.pages.dev/)
  - [Spotify API を使った音楽検索アプリ](https://spotify-api-app.pages.dev/)
- オリジナルアプリ [リブラク](https://libraku.pages.dev/) の制作に着手

## 6 月

- 【継続】オリジナルアプリ [リブラク](https://libraku.pages.dev/) の制作・v1 のリリース
  - ルーティング(React Router)について学ぶ
  - useContext を利用してキャッシュを行い、キャッシュの仕組みについて学ぶ
  - ReactQuery や useSWR を使用したキャッシュ方法について学ぶ
  - セキュアにデータを扱うために API を建てる
  - React Hook Form と Yup/Zod を使用したフォーム作成を学ぶ
  - Resend を使用したメール送信の方法を学ぶ
    - メールの仕組み（メールサーバや DNS レコードなど）について調査する
- 『プロになるための Web 技術入門』5 章まで
- 『フロントエンドの知識地図』読了

## 7 月

- 【継続】オリジナルアプリ [リブラク](https://libraku.pages.dev/) v2 の制作
  - shadcn/ui を使った UI のコンポーネント化
  - Framer Motion を使って簡単なアニメーションを実装
  - お問い合わせページに Cloudflare Turnstile を追加し、BOT からのメール防止の実装
  - Cloudflare D1, Drizzle ORM, Lucia Auth を使って認証機能を実装
  - 同一オリジンとして Cookie を扱うため、本番環境用のプロキシサーバーを functions, \_routes.json で設定
- Hono, Workers, Pages Functions を調査
- Session ID, Cookie を使った認証の方法を調査
- ハッシュ化, バリデーションについて調査
- OAuth, Open ID Connect, JWT について調査
- Basic 認証, Digest 認証, Bearer 認証について調査
- 練習用リポジトリにて、JWT のアクセストークンとリフレッシュトークンを実装（ブラックリストは未実装）
- React Query の useMutation を使った fetch 処理について調査
- Cookie の設定項目について調査
- 『Web 技術の基本』 読了

## 8 月

- 【継続】オリジナルアプリ [リブラク](https://libraku.pages.dev/) 制作
  - 利用者番号登録機能の実装
  - お気に入り機能の実装
  - PWA の設定
  - メールアドレス, パスワード変更機能の実装
    - 検証コードの実装
- 共同プロジェクト [LGTM Factory](https://github.com/lgtm-factory/lgtm-factory) の開発開始
  - コードレビューを積極的に行う
    - 人の書いたコードを読む力を身に付ける
    - テキストコミュニケーション能力を身に付ける
  - Next.js と TypeScript のキャッチアップ
- 技術記事を書く

## 9 月

- 【継続】共同プロジェクト [LGTM Factory](https://github.com/lgtm-factory/lgtm-factory) に継続参加・v1 リリース
  - Next.js の Route Handler, SSG 化, cache, fetch について深掘る
  - 『実践 Next.js』途中まで
- 【継続】オリジナルアプリ [リブラク](https://libraku.pages.dev/) 制作・v2 リリース
  - バグ修正
  - リファクタリング
  - README の整備
  - v2.1 の実装
    - Cron Trigger の実装
    - SEO 対策
  - テスト手法について調査

## 10 月

- 就活（企業調査、履歴書・職務経歴書作成）
- フロントエンドのテストについて調査
- 『フロントエンド開発のためのテスト入門』を読む
- 帰省中の空き時間に『プリンシプル・オブ・プログラミング』を読む

## 11 月

- 就活（SPI、面接）

## 🚀 これからの予定

## 12 月

- 就活
- Udemy『JavaScript メカニズム』
- Udemy『Node.js 完全入門ガイド』
- 『TypeScript 詳解実践ガイド』
- 『Web を支える技術』
