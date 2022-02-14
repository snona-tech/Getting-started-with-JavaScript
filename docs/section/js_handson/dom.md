## DOM (Document Object Model)

HTMLなどの文書を表現・操作する方法。<br>
DOMでJavaScriptからHTMLの要素を生成したり、値を取得することができる。

## HTML要素の取得

操作対象の要素をJavaScriptで取得する。<br>
よく使用する関数について記載する。

| 関数名                 | 引数          | 戻り値                                |
| ---------------------- | ------------- | ------------------------------------- |
| getElementsByTagName   | タグ名        | HTML要素の配列                        |
| getElementsByClassName | クラス名      | HTML要素の配列                        |
| getElementById         | id属性        | HTML要素                              |
| getElementsByName      | name属性      | HTML要素の配列                        |
| querySelector          | CSSセレクター | CSSセレクターに一致する最初のHTML要素 |
| querySelectorAll       | CSSセレクター | CSSセレクターに一致するHTML要素の配列 |

!!! example "使用例"

    bodyタグを取得してコンソールに表示。

    ```javascript
    let body = document.getElementsByTagName('body')[0];
    console.log(body);
    ```

## HTML要素の編集

HTML要素はプロパティを保持しており、プロパティを編集することで要素の編集を行う。<br>
`innerText`プロパティは要素内のテキスト、`innerHTML`プロパティは要素内のHTMLを指している。

!!! example "使用例"

    bodyタグ配下を`<h1>タイトル</h1>`に変更する。

    ```javascript
    let body = document.getElementsByTagName('body')[0];
    body.innerHTML = '<h1>タイトル</h1>';
    ```

    h1タグのタイトルのテキストを編集

    ```javascript
    let title = document.getElementsByTagName('h1')[0];
    title.innerText = 'Javascriptを学ぼう！';
    ```

## HTML要素の生成

今までは既に存在するHTML要素を取得してプロパティから要素の変更を行なったが、これでは要素内を丸ごと書き換えてしまうため元々存在していた子要素などが消えてしまう。<br>
要素の追加は`createElement`で要素を作成し、必要であれば`setAttribute`で属性の付与を行なった上で要素の追加を行う。

!!! example "使用例"

    bodyタグ配下を`<h1>タイトル</h1>`に変更する。

    `div#main`を生成し、その配下に`label[for='new-input'], input#new-input[type='text']`を追加する。

    ```javascript
    // div、label、input 要素を生成
    let newInput = document.createElement('input');
    newInput.setAttribute('id', 'new-input');
    newInput.setAttribute('type', 'text');

    let newLabel = document.createElement('label');
    newLabel.setAttribute('for', 'new-input');
    newLabel.innerText = '文字入力：';

    let newDiv = document.createElement('div');
    newDiv.appendChild(newLabel);
    newDiv.appendChild(newInput);

    // bodyに生成した要素を追加
    let body = document.getElementsByTagName('body')[0]
    body.appendChild(newDiv);
    ```

### 追加位置

`appendChild`は要素内で一番下に子要素を追加する。他にも要素の追加位置を制御する関数があるので紹介する。

| 関数名       | 挿入する位置                                                      |
| ------------ | ----------------------------------------------------------------- |
| appendChild  | 指定したHTML要素の中の末尾に挿入する                              |
| before       | 指定したHTML要素の前に挿入する                                    |
| after        | 指定したHTML要素の後に挿入する                                    |
| insertBefore | 指定したHTML要素の中にある、第2引数で指定した子要素の前に挿入する |

## HTML要素の値取得

上記の節で見たように、`innerText`プロパティの値は`<タグ名>XXX</タグ名>`の`XXX`の部分に相当する。<br>
他にも、`input`タグや`select`タグの入力値は`value`プロパティから取得できる。

!!! example "使用例"

    入力欄(input)に入力された値を取得する。

    1. 入力欄を生成する。

        ```javascript
        let newInput = document.createElement('input');
        newInput.setAttribute('type', 'text');
        let body = document.getElementsByTagName('body')[0]
        body.appendChild(newInput);
        ```

    2. ブラウザから値を入力する。
    3. `value`プロパティから値を取得する。

        ```javascript
        console.log(newInput.value);
        ```

## HTML要素の削除

`HTML要素.remove()`で削除できる。<br>
また、`removeAttribute`や`removeChild`で属性や子要素のみ削除することも可能。
