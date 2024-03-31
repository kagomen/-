## 0322
### プログラミング学習
  - GitHubのデコり方調べた
    - プロフィールページにバッジつけたりステータスつけたりした
  - [React Foundations -Next.js](https://nextjs.org/learn/react-foundations)
    - 最初から最後まで
  - [Learn Next.js -Next.js](https://nextjs.org/learn/dashboard-app)
    - Chapter1~3
    - [clsx](https://github.com/lukeed/clsx): 条件付きでclassを指定したいときに使うライブラリ
    - [CLS](https://web.dev/articles/cls?hl=ja): 読み込みの際にビューにズレが生じないかの指標
    - Safariなどでフォントが太い場合、tailwindで`antialiased`を指定すると改善される可能性

### メモ
  - https://tailwindcss.com/docs/utility-first
    - Tailwindの思想　明日読む 
  - https://react.dev/learn
    - Next.jsのチュートリアル終わったらReactのチュートリアルもやりたい

### 調べた英単語・熟語
  - Prerequisite 前提条件
  - assume 想定する
  - collision 衝突
  - Suppose that と仮定する
  - Fallback
  - prevent　予防する
  - identical 同一の
   
### 感想
  - チュートリアルをGoogle翻訳かけたらあまりにもひどいので、頑張って原文読んでみたら案外読めた。
  - このまま原文で読み続けて、英文への抵抗をなくしていきたい！ 

## 0323
### プログラミング学習
  - [Learn Next.js -Next.js](https://nextjs.org/learn/dashboard-app)
    - Chapter4 Creating Layouts and Pages
      - `layout.tsx`で記述した部分は`{children}`がレンダリングされても再レンダリングされない
    - Chapter5 Navigating Between Pages
      - Linkコンポーネントを使用するととcode-splitingとprefetchが適用される
      - prefetchは本番環境でのみ適用され、開発環境では適用されない
      - prefetchが適用されると戻るボタン・進むボタンをクリックしても、スクロール位置が記録される
      - `usePathname`とclsxを利用して、activeなリンクにスタイルを当てることができる
    - Chapter6 Setting Up Your Database
      - seeding: データベースに初期データを入れること
    - Chapter7 Fetching Data
      - データを取得する方法
        - API layer
        - Databaseにクエリ文で問い合わせる
        - Server Components
  - GitHubのデコり方の調査
    - sheilds.ioのサービス使ってバッジ作ってみた
    - myOctcatのアバター作った

### メモ・その他
  - なし

### 調べた英単語・熟語
  - reveal 明らかにする
  - sibling 兄弟姉妹
  - likelihood　可能性、もっともらしさ、尤度関数
  - conditionally 条件付きで
  - implement 実装する
  - versatile 用途が広い
  - discriminate 差別する、判別する
  - manipulate 操作する

### 感想
  - 今日はドキュメントも英語で読んでみたけど難しかった。また、Chapter6からサーバーサイドの分野に入ったが、昨日のようにはスラスラ読めなかったし、かなりDeepL使った。昨日「読めた」と感じたのは、内容を推測しながら読んでたからなんだろうな……。ちょっとガッカリ。まあでも、原文で読むのは習慣化させたい。
  - Next.jsが多・高機能すぎてビビる。
  - README用のアクセスカウンター作りたい。

## 0324
### プログラミング学習
- Udemy Node.js入門
  - 相対パス：`./<ディレクトリ名>` or `<ディレクトリ名>`
    - `../`は親ディレクトリ
  - 絶対パス：`/<ディレクトリ名>`
  - `__dirname`: 現在のファイルが格納されたディレクトリまでの絶対パス
  - `__filename`: 現在のファイルまでの絶対パス
  - `path.resolve()`: 引数に絶対パスを入れると、前のパスが無視される
  - モジュール管理は2通り
    - CJS: Node.js独自の記法（`package.json`でESMを設定した際は拡張子を`.cjs`にする）
    - ESM: 現在はこちらが推奨されている（`package.jsonで設定` or 拡張子を`.mjs`にする）

### メモ
- 

### 調べた英単語・熟語
- 

### 感想

## 0331

- [【HTTP入門】Webページがブラウザに表示されるまでの流れを解説](https://www.youtube.com/watch?v=b_apIgHNqtk)
  - URLを入力
  - キャッシュにあるIPアドレスを取得
    -> キャッシュになければDNSサーバでIPアドレスを取得する
  - ポート番号を割り当てる　`<IPアドレス>:443`
    - ポート番号は通信するデータの種類によって異なる
      - HTTP -> 80
      - HTTPS -> 443
  - WebサーバにHTTPリクエストを送る
      ```
      ** HTTPリクエストのフォーマット **
      
      リクエストライン // メソッドなど
      ヘッダー
      空行
      メッセージボディ // GETの場合はメッセージボディはない
      ```
   - ロードバランサーでアクセスを調整する
   - クライアントにHTTPレスポンスを送る
      ```
      ** HTTPレスポンスのフォーマット **
      
      ステータスライン // ステータスコードなど
      ヘッダー
      空行
      メッセージボディ // HTMLデータなど
      ```
   - レンダリングする
      1. Loading: HTMLの読み込み -> CSSの読み込み
      2. Scripting: JavaScriptの読み込み
      3. Rendering: --
      4. Painting: レンダリングしたものを画面に映し出す

[【CORS入門】もうCORSエラーに苦しむことはありません。Webエンジニア必見です。](https://youtu.be/8fE2TmbPqlU?si=s7_qrkMQCH6pBv9X)
- CORSとは: オリジン間リソース共有
- Webは同じオリジン間でしかリソースの共有を許可していない
  -> 開発時にフロントとバックでそれぞれサーバを立ててデータ共有しようとするとCORSエラーが起こる
  -> サーバ側で別オリジンからのリクエストを許可する必要がある
  ```
  npm i cors
  ```
  ```node
  const cors = require("cors");

  app.use(cors({
    origin: "http://127.0.0.1:5500", // どのオリジンからのアクセスを許可するか
    methods: ["GET", "POST"], // どのメソッドを許可するか
    credentials: true, // クッキーを許可するか
  }))
  ```
  

- ドットインストール Node.js入門

***

```
## 
### プログラミング学習
- 

### メモ
- https://youtu.be/o9YLtvlk8oc?si=RSsxOtHez9k-NFTD
- 

### 調べた英単語・熟語
- 

### 感想
- 
```
