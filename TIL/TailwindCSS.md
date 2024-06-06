## Tailwind CSS

- クラス名を動的に生成する場合、注意が必要

  - NG: `text-${red}-600`
  - OK: `${text-red-600}`
  - 以下も OK
    ```js
    const Button = ({ text, color = "sky" }) => {
      const colorVariants = {
        sky: "border-sky-500 ",
        orange: "border-orange-500 ",
      };
      return (
        <button className={`border-2 ${colorVariants[color]}`}>{text}</button>
      );
    };
    ```
  - 参考: https://tailwindcss.com/docs/content-configuration#dynamic-class-names

- body で Tailwind を使いたい場合は、下記のように指定する

  ```css
  @tailwind base;
  @tailwind components;
  @tailwind utilities;

  @layer base {
    body {
      @apply font-sans text-black;
    }
  }
  ```
