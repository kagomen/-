## React

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
