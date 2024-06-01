# Sass(SCSS)

- @forward

  - ファイルを呼び出して展開する
  - 中継ファイルなどで使用する

- @use

  - 名前空間を保ったままファイルを呼び出す
  - `@use '<ファイル名>' as *;`でファイルを呼び出すと、`@forward`のような使い方ができる
  - パーシャルファイルは、呼び出し時は`_`と`.scss`を省略できる

- パーシャルファイル

  - `_<ファイル名>.scss`とすることで、css ファイルを吐き出さない sass ファイルになる

- settings.json

  - 吐き出す css ファイルのディレクトリを指定する

- @mixin

  - コンポーネントのような形で css を定義する
  - `@mixin button {...}`と定義する
  - 使用する際は`@include button`と呼び出す
  - `@mixin button($color)`などとして、引数の設定が可能
    - `@mixin button($color: blue)`としてデフォルト値の設定も可能

```
npm i -D sass
```

```
// package.json

  "scripts": {
    "sass": "sass src/sass/style.scss build/css/style.css --watch"
  },
```

```
npm run sass
```
