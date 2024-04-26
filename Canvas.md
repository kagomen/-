## Canvas

- arc(x, y, r, startAngle, endAngle, anticlockwise)

  - (x, y) を中心とし、半径 r の円を startAngle から endAngle まで描く。
  - anticlockwise はデフォルトでは false となっている。true とした場合も、startAngle や endAngle の方向は時計回りとなるので注意。（描画時の方向のみ反時計回りとなる）

- 高解像度化

  ```js
  const dpr = window.devicePixelRatio || 1; // dprに対応していないPCの場合、1を返す
  const CANVAS_WIDTH = canvas.width;
  const CANVAS_HEIGHT = canvas.height;
  canvas.width = CANVAS_WIDTH * dpr;
  canvas.height = CANVAS_HEIGHT * dpr;
  g.scale(dpr, dpr);
  canvas.style.width = `${CANVAS_WIDTH}px`;
  canvas.style.height = `${CANVAS_HEIGHT}px`;
  ```

- 時計を描画する

  ```js
  for (let i = 0; i < 12; i++) {
    // 座標を保存
    g.save();

    // 座標を移動
    g.translate(200, 200);

    // 回転
    let r = ((2 * Math.PI) / 12) * i;
    g.rotate(r);

    g.beginPath();
    g.moveTo(0, 100);
    g.lineTo(0, -50);
    g.stroke();

    // 座標をsave地点まで呼び戻す
    g.restore();
  }
  ```
