# Webpack

### 初期設定

```
npm init -y
npm i -D webpack webpack-cli webpack-dev-server
```

以下のようにコマンドで設定・実行もできる

```
npx webpack --mode development
```

しかし基本的には webpack.config.js で設定し、

```js
// webpack.config.js

module.exports = {
  mode: "development",
};
```

```
npx webpack
```

で実行する

npm で実行したい場合は、package.json の scripts にコマンドを記載する必要がある

```json
// package.json

  "scripts": {
    "webpack": "webpack"
  },
```

これで

```
npm run webpack
```

で実行できるようになる

### entry

- エントリーポイントが一つの場合

  ```js
  // webpack.config.js

  module.exports = {
    entry: "./src/app.js",
  };
  ```

- エントリーポイントが複数の場合

  ```js
  // webpack.config.js

  module.exports = {
    entry: {
      app: "./src/app.js",
      sub: "./src/sub.js",
    },
  };
  ```

### output

出力先のディレクトリや出力するファイル名を設定
（デフォルトは `dist/main.js`が出力される）

```js
const path = require("path");

module.exports = {
  output: {
    path: path.resolve(__dirname, "public"),
    filename: "[name].js",
  },
};
```

上記の場合、public フォルダの中に、entry で設定したキー名の js ファイルが出力される

### loader とは

JS ファイル以外をバンドルするには loader が必要
（JS で load するには loader が必要ということ？）

```
npm i -D sass sass-loader css-loader style-loader
```

```js
// webpack.config.js

module: {
  rules: [
    {
      test: /\.scss$/, // 対象を記載
      use: [
        // 処理内容を記載（下から順に実行される）
        "style-loader", // css -> html
        "css-loader", // 複数のcssをバンドル
        "sass-loader", // sass -> cssに変換
      ],
    },
  ];
}
```

```js
// app.js

import "./app.scss";
```

このようにして読み込むと、index.html で css を読み込まなくてもスタイルが適用される

### postcss-loader

```
npm i -D postcss-loader autoprefixer
```

```js
// postcss.config.js

module.exports = {
  plugins: [
    require('autoprefixer)
  ]
}
```

```js
// webpack.config.js

module: {
  rules: [
    {
      test: /\.scss$/, // 対象を記載
      use: [
        // 処理内容を記載（下から順に実行される）
        "style-loader", // css -> html
        "css-loader", // 複数のcssをバンドル
        "postcss-loader", // cssにautoprefixerを付与
        "sass-loader", // sass -> cssに変換
      ],
    },
  ];
}
```

### file-loader

```
npm i -D file-loader
```

option を設定する時は{}を追加して以下のように記述

```js
module: {
  rules: [
    {
      test: /\.(jpe?g|gif|png|svg|woff2?|ttf|eot)$/,
      use: [
        {
          loader: "file-loader",
          options: {
            name: "[name].[ext]",
            outputPath: "images", // dist/imagesが生成され、その配下にファイルが配置される
            publicPath: "images",
          },
        },
      ],
    },
  ];
}
```

ただしローダーが一つしかない時は以下のように省略が可能

```js
module: {
  rules: [
    {
      test: /\.(jpe?g|gif|png|svg|woff2?|ttf|eot)$/,
      loader: "file-loader",
      options: {
        name: "[name].[ext]",
        outputPath: "images",
        publicPath: "images",
      },
    },
  ];
}
```

ソースコードを置いているサーバーに画像を配置しているのであれば publicPath は outputPath で OK
CDN を利用している場合は、publicPath に CDN の URL を指定する

```js
name: "[contenthash].[ext]";
```

上記のようにすると、ファイル名をハッシュ値にできる

- hash
  - ビルド毎に同じハッシュ値が付与される
  - 一つのファイルを更新するとすべてのファイル名が変更される
- contenthash
  - ファイル毎にハッシュ値が付与される
  - 画像ファイルなどに使われる
- chunkhash
  - output 毎に同じハッシュ値が付与される
  - js/css ファイルなどに使われる

### babel-loader

```
npm i -D babel-loader @babel/core @babel/preset-env
```

```js
module: {
  rules: [
    {
      test: /\.js$/,
      exclude: /node_modules/,
      loader: "babel-loader",
    },
  ];
}
```

```
npm i -D core-js@3 regenerator-runtime
```

```js
// babel.config.js

module.exports = (api) => {
  api.cache(true);

  return {
    presets: [
      [
        "@babel/preset-env",
        {
          targets: {
            browsers: [
              "last 1 version",
              "> 1%",
              "maintained node versions",
              "not dead",
            ],
          },
          useBuiltIns: "usage",
          corejs: 3,
        },
      ],
    ],
  };
};
```

- regenerator-runtime
  - async await を補完
- core-js
  - それ以外を補完

https://zenn.dev/sa2knight/articles/67f6f5cc4ed5e26e391c

### webpack-dev-server

- `webpack -w`

  - ファイルの変更を監視し、変更があるたびに自動的にビルドを実行する

- webpack-dev-server
  - 開発用サーバーを提供
  - Hot Module Replacement（HMR）を提供
    - ファイル変更時、ブラウザをリロードすることなく変更をリアルタイムに反映する

## ESLint & Prettier & Husky

```torahack
npm i -D eslint eslint-config-prettier prettier @typescript-eslint/parser @typescript-eslint/eslint-plugin husky lint-staged
```

```mu-zaru
npm init @eslint/config
```

```codemafia
npm i -D eslint eslint-webpack-plugin @babel/eslint-parser
```

npm i -D eslint eslint-webpack-plugin

```codemafia
// .eslintrc

{
  "env": {
    "browser": true,
    "es2017": true
  },
  "extends": "eslint:recommended",
  "parser": "babel-eslint"
}
```

```js
// .prettierrc

{
  "printWidth": 120,
  "singleQuote": true,
  "semi": true
}
```

```js
// .eslintrc.js

module.exports = {
  env: {
    browser: true,
    es6: true,
  },
  extends: [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended", // TypeScriptでチェックされる項目をLintから除外する設定
    "prettier", // prettierのextendsは他のextendsより後に記述する
    "prettier/@typescript-eslint",
  ],
  plugins: ["@typescript-eslint"],
  parser: "@typescript-eslint/parser",
  parserOptions: {
    sourceType: "module",
    project: "./tsconfig.json", // TypeScriptのLint時に参照するconfigファイルを指定
  },
  root: true, // 上位ディレクトリにある他のeslintrcを参照しないようにする
  rules: {},
};
```

```json
// package.json
  "scripts": {
    "lint": "eslint --fix 'src/**/*.{js,ts}'",
    "lint-fix": "eslint --fix './src/**/*.{js,ts}' && prettier --write './src/**/*.{js,ts}'"
  },
```

```json
// package.json

  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "src/**/*.{js,jsx,ts,tsx}": [
      "npm run lint-fix"
    ]
  }
```
