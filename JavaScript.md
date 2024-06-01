# JavaScript

- 配列操作メソッド

  - reduce()

    ```js
    const arr = [1, 2, 3, 4];

    const sum = arr.reduce((sum, num) => {
      return sum + num;
    }, 0);

    // 0はsumの初期値
    ```

  - concat()

    ```js
    const arr1 = ["a", "b", "c"];
    const arr2 = ["d", "e", "f"];
    const arr3 = arr1.concat(arr2);

    // arr3 = ["a", "b", "c", "d", "e", "f"];
    ```

  - structuredClone()
    - 多次元配列の場合、スプレッド構文ではネストされた配列はクローンされない。
    - `structuredClone()`はネストされた配列まで一気にクローン可能。

- ES Module

  - 便利な特徴
    - `'use strict';`を宣言せずに strict モードが適用される
    - `defer`がデフォルトで適用される
    - モジュール空間
    - import 文が使える
  - 注意点

    - ファイルの階層が同じでも明示する必要がある
      ```
      // 同一階層の foo.js を取得
      import foo from './foo.js';
      // 上の階層の bar.js を取得
      import bar from '../bar.js';
      // ルートパスの baz.js を取得
      import baz from '/baz.js';
      // 以下は無効
      import foo from 'foo.js';
      ```
    - webpack を導入しないと import 時のファイルの拡張子は省略不可
    - `var`は使用不可

  - サイドエフェクトインポート
    - ただファイルを実行する
    ```js
    import "./foo.js";
    ```

- localStorage

  - クライアントサイドでのみデータの使用が可能
  - 永続的にデータを保存する

  ```js
  localStorage.setItem("keyName", "value");
  localStorage.getItem("keyName");
  ```

  - 注意点
    - localStorage に set した値はすべて文字列に変換されるので、数字や真偽値を扱う際は注意する

- sessionStorage

  - クライアントサイドでのみデータの使用が可能
  - ブラウザを閉じるとデータは破棄される

- cookie

  - クライアントサイドとサーバーサイドの両方でデータの使用が可能
  - データの保存期間を設定できる

- fill()

  - `new Array(3)` などで生成した**値を持たない配列**に対し、値を持たせる関数

  ```js
  // NG例
  Array(20).map(() => {...})

  // OK例
  Array(20).fill().map(() => {...})
  ```

  > callback は、値が代入されている配列のインデックスに対してのみ呼び出されます(undefined が代入されているものも含みます)。すでに削除されたインデックスや、まだ値が代入されていないインデックスに対しては呼び出されません。

  - 参考: https://yucatio.hatenablog.com/entry/2019/04/07/110721

- static

  - クラス定義の中で、インスタンス化せずに直接呼び出せるメソッドやプロパティにつける接頭辞

- クラス内で定義するメソッドを宣言するときは、function を省略する

- json()

  - 非同期処理なので、await をつける

- トップレベル await

  - ES2022 からトップレベルで await を使用する際は、async 関数で囲う必要がなくなった
  - それ以前は即時実行関数を利用するなどして、半ば強引に（？）実行していた

- getBoundingClientRect()
  要素の情報(top, left, bottom, right の座標など)を得る

- DOMContentLoaded イベント

  - ページのロード・解析を終えたタイミングでコードを実行する

- load イベント

  - ページの解析・画像・スタイルシートなど、付随する全コンテンツのロードを終えたタイミングで実行する

- defer 属性

  - 非同期で js ファイルをロード、ページのロード・解析が終わったタイミングで js ファイルを実行
  - `type="module"`にした場合、defer 属性は記載せずとも自動的に付与される

- 再エクスポート
  - 複数のモジュールをまとめて export する中核のモジュールを作る
  ```
  export {hoge} from './hoge.js';
  export {fuga} from './fuga.js';
  ```
