# React

- イベントハンドラへの関数の渡し方

  1. `onClick = {hoge}`
  1. `onClick = {() => hoge()}`

  - `onClick = {hoge()}`とするとレンダリング時に実行される
  - そのため、実行する関数が引数をとるときは 2 の書き方を採択することになる
  - `onClick = {(e) => hoge(e.target.value)}`
  - JavaScript では、HTML 内で onclick を使用する際は`<button onclick="hoge()">ボタン</button>` とするので注意

- useRef

  - レンダリングせずに値を保持する
  - useState のようにレンダリングする必要がなければ useRef を使用する

- useState はレンダリング時に state の値を更新する

  ```js
  const [page, setPage] = useState(1);

  export function App(props) {
    const countUp = () => {
      setPage((prev) => prev + 1);
      console.log(page); // 1が表示される
    };
    return (
      <span>{page}</span> // 2が表示される
    );
  }
  ```

  - 解決策 1. useState と一緒に useEffect を使う

  ```js
  const countUp = () => {
    setPage((prev) => prev + 1);
  };

  useEffect(() => {
    console.log(page);
  }, [page]);
  ```

  - 解決策 2. 値を直接代入する

  ```js
  const countUp = () => {
    prevPage = page + 1;
    console.log(prevPage);
    setPage(prevPage);
  };
  ```

- useEffect に async をつけて非同期処理にするとエラーになる
  - useEffect はコールバック関数にクリーンアップ関数を返すことを期待している（指定しない場合は`undefined`となる）
  - async 関数は常に Promise を返すため、useEffect が期待するシグネチャと一致しない
  ```js
  useEffect(() => {
    (async () => {
      const res = await fetch(URL);
      const data = await res.json();
      console.log(data);
    })();
  }, []);
  ```

## useState, useContext, 状態管理ライブラリの比較

- useState
  - 状態が変化すると、props のバケツリレーを行った親コンポーネントすべてが再レンダリングされる
- useContext
  - 状態を受け取る子コンポーネントだけが再レンダリングされる
  - `useContext`のファイルが膨大になる
    - 1 ファイルに状態をまとめると、1 つの状態が変化しただけでも、ファイルにまとめた状態を持つコンポーネントはすべて再レンダリングされる
  - useState と比べるとテストがしにくい
- 状態管理ライブラリ
  - ひとつのファイルで複数の状態を管理できる
    - useContext と異なり、変化した状態を使用しているコンポーネントのみ再レンダリングされる
  - useContext と同じくテストはしにくい
- https://blog.uhy.ooo/entry/2021-07-24/react-state-management/
