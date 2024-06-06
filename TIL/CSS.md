# CSS

- `align-items: center;`

  - `display: flex;` と一緒に使う
  - **縦軸**の指定
  - 親要素（自分） => 子要素へ指定

- `justify-content: center;`

  - `display: flex;` と一緒に使う
  - 親要素（自分） => 子要素へ指定
  - **横軸**の指定

- `text-align: center;`

  - **横軸**の指定
  - ブロック要素（自分） => インライン要素へ指定

- `vertical-align: middle;`

  - **縦軸**の指定
  - 数字で指定も可能
  - 子要素（自分） => 親要素へ指定

- `<button>`の中央寄せ

  1. `<div>`で囲って`<div>`に`text-align: center;`を指定
  1. `display: block; margin: 0 auto;`

- `display: flex;`

  - 子要素を横並びにする
  - 子要素をブロック要素に変化させる

- `width: fit-content;`

- セレクター

  - 属性セレクター
    - `[target] { ... }`
    - `[type="text"] {...}`
  - 複合セレクター
    - `div.box {...}`
  - 子結合子
    - `section > p {...}`
      - section の子要素の p を指定
  - 子孫結合子
    - `section p {...}`
      - section の子孫要素の p を指定
  - 隣接兄弟結合子
    - `li + li {...}`
      - li の 2 番目以降の全ての要素を指定
  - 擬似クラス
    - `li:hth-child(3) {...}`
      - li の 3 番目を指定
    - `li:nth-child(odd) {...}`
      - li の奇数番目を指定
    - `li:nth-child(even) {...}`
      - li の偶数番目を指定
    - `li:nth-child(2n) {...}`
      - li の 2 の倍数番目を指定
    - `li:first-child {...}`
      - li の最初の要素を指定
    - `li:last-child {...}`
      - li の最後の要素を指定
    - `input:focus {...}`
      - input の focus 時を指定
    - `div:not(.box) {...}`
      - box クラス以外の div を指定
  - 擬似要素
    - `p::before {content: '- ';}`

- CSS 変数

  ```
    :root {
      --base-color: gray;
    }

    body {
      background: var(--base-color);
    }
  ```

- z-index

  - position 指定された要素や flex 要素にしか効かない

- CSS nesting

  - ほとんどのブラウザで使用可能！
  - https://caniuse.com/?search=css%20nest
  - 少し前のバージョンの Safari は未対応なのでユーザーが Safari をアップデートしていない場合、CSS が反映されない

- touch-action: manipulation;

  - スマホでのダブルタップ時にズームされるのを無効にする

- dvh

  - iPhone の Safari で下に URL ボックスが表示され、`vh`が思い通りに機能をしないのを防ぐ
  - https://webrandum.net/ios-safari-dvh/

- -webkit-user-select: none;

  - Safari だと`user-select: none;`が効かない

- -webkit-touch-callout: none;

  - 画像などを長押しした際に出現するポップアップを無効にする

- hidden

  > ウェブブラウザーは display: none を使用して hidden 状態を実装することができ、その場合、その要素はページレイアウトに参加しません。これはまた、hidden 状態の要素で CSS の display プロパティの値を変更すると、その状態が上書きされるということでもあります。例えば、display: block とスタイル設定された要素は、hidden 属性があるにもかかわらず、表示されることになります。

  `display: flex`なども同様で、`flex`を使用している要素に`hidden = true`としても実行されない

- `p .title`
  - p タグの子要素の title クラスを指定
- `p.title`

  - title クラスを持つ p タグを指定

- `@import`を使うメリット

  - html がすっきりする
  - ファイルごとに`@charset: 'UTF-8';`を書かなくて済む

- Autoprefixer

  - サポート対象にしたいブラウザを設定すると自動的にベンダープレフィックス（-webkit-, -moz-, -ms-）を付け、必要であれば構文の変更もしてくれるツール

    | -webkit- | Google Chrome, Safari |
    | -moz- | Firefox |
    | -ms- | IE |
