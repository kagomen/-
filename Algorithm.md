# アルゴリズム

- Fisher–Yates shuffle

```js
Array.prototype.shuffle = function () {
  let currentIndex = this.length;
  while (currentIndex != 0) {
    const randomIndex = Math.floor(Math.random() * currentIndex);
    const temp = this[currentIndex - 1];
    this[currentIndex - 1] = this[randomIndex];
    this[randomIndex] = temp;
    currentIndex--;
  }
  return this;
};
```
