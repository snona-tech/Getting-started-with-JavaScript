## HTMLファイルにJavaScriptを導入する

導入方法は大きく２つある。

* [x] `script`タグ内に直接JavaScriptを記述する
* [x] `.js`ファイルを読み込む

基本的にどちらの方法でもよいが、機能別あるいは画面別にJavaScriptファイルを分割した方がメンテナンス性を考慮してファイルを読み込む方式で行うことが望ましい。

## JavaScriptの読み込み順

JavaScriptに限らず、多くのプログラミング言語は上から下に順に実行される。HTMLに関しても基本的にはブラウザで上から順に描画されていく。<br>
処理順を意識しないと、意図した通りの動作にならないことがあるため注意が必要。

### 記述位置と読み込み順の制御

まずは次のHTMLとJavaScriptを作成し、ブラウザで表示してみる。

```html title="index.html" hl_lines="14-15"
<!DOCTYPE html>
<html lang="ja">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <button id="test-alert">アラートを表示</button>

    <!-- bodyの終了タグ直前に記述 -->
    <script src="load.js"></script>
</body>

</html>
```

```javascript title="load.js"
// ボタン要素を取得
let elm = document.getElementById('test-alert');
console.log(`取得した要素： ${elm}`);

// クリックイベントにアラート表示処理を設定
elm.addEventListener('click', () => alert('Hello JavaScript!'));
```

`button`タグのクリック時の動作（イベント）を`addEventListener`で設定しているため、`アラートを表示`ボタンを押すとアラートダイアログが表示される。<br>
イベントについては次の章で説明する。

今度は、JavaScriptの記述位置を以下のようにheadタグ内に記述する。

```html title="index.html" hl_lines="10-11"
<!DOCTYPE html>
<html lang="ja">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <!-- headタグ内に記述 -->
    <script src="load.js"></script>
</head>

<body>
    <button id="test-alert">アラートを表示</button>
</body>

</html>
```

`アラートを表示`ボタンを押しても何も表示されなくなる。<br>
これは、`button`タグが生成される前に`button`タグにクリックイベントを設定しようとしたことが原因。

このような事象を回避するためには処理順を意識してJavaScriptの記述位置を調整するか、画面の読み込みが完了した後にJavaScriptを読み込むようにプログラムで制御する必要がある。

### onloadプロパティ

`window.onload`プロパティにハンドラー関数を設定することで画面の読み込みが完了した後にJavaScriptの読み込みを行うことができる。

!!! note "構文"

    ```javascript
    window.onload = () => {
        // JavaScriptの処理
    };
    ```

次のようにJavaScriptを書き換えてみると、正しくクリックイベントが設定できる。

```javascript title="load.js"
window.onload = () => {
    // ボタン要素を取得
    let elm = document.getElementById('test-alert');
    console.log(`取得した要素： ${elm}`);

    // クリックイベントにアラート表示処理を設定
    elm.addEventListener('click', () => alert('Hello JavaScript!'));
};
```