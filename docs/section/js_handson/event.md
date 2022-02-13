## イベントの登録

イベントはHTML要素に対してクリックのようなマウス操作などを契機に処理を実行できる仕組みであり、Webサイトに動きをつけるために必須の技術である。<br>
イベントの種類については「[イベント](https://developer.mozilla.org/ja/docs/Web/API/Element#events)」を参照。

!!! note "構文"

    ```javascript
    要素.addEventListener(イベントの種類, e => {
        // イベント発火時の処理
    });
    ```

!!! example "使用例"

    入力欄にフォーカスした時にメッセージを表示する。

    ```html title="index.htmlのbody"
    <label for="test-input">お名前：</label>
    <input type="text" name="test-input" id="test-input">
    <div id="note"></div>
    ```

    ```javascript title="event.js" hl_lines="5-8 10-13"
    window.onload = () => {
        let testInput = document.getElementById('test-input');
        let note = document.getElementById('note');

        // 入力欄にフォーカスした時にメッセージを表示
        testInput.addEventListener('focus', () => {
            note.innerText = '苗字と名前の間に半角スペースを入れてください。'
        });

        // 入力欄からフォーカスが外れた時にメッセージを削除
        testInput.addEventListener('blur', () => {
            note.innerText = ''
        });
    };
    ```
