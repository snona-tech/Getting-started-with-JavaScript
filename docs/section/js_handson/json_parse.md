## パース

パース(parse)は、決まった書式や文法に従って構文を解析すること。<br>
HTTP通信などではしばしばJSON形式のデータをやり取りするため、受信したデータの整形や画面表示用の加工処理などをJavaScriptで行う必要がある。

!!! note "構文"

    JSONオブジェクトの作成。

    ```javascript
    JSON.parse(JSON文字列);
    ```

!!! example "使用例"

    JSON文字列からJSONオブジェクトを作成し、年齢と趣味の2番目の要素を取得してコンソールに表示する。

    ```javascript
    const jsonStr = `{
        "id": 1,
        "name": "ジャバ　スクリプト",
        "age": 25,
        "hobby": [ "スカッシュ", "料理", "テレビドラマ" ]
    }`;
    const jsonObj = JSON.parse(jsonStr);

    let age = jsonObj.age;
    let secondHobby = jsonObj.hobby[1];

    console.log(`年齢： ${age}`);
    console.log(`二番目の趣味： ${secondHobby}`);
    ```

    `JSON.parse`の第二引数に関数を設定することで、オブジェクトに変換する前にJSONの加工ができる。<br>
    下の例は、年齢の値だけ+1する加工を入れている。

    ```javascript
    const jsonStr = `{
        "id": 1,
        "name": "ジャバ　スクリプト",
        "age": 25,
        "hobby": [ "スカッシュ", "料理", "テレビドラマ" ]
    }`;
    const jsonObj = JSON.parse(jsonStr, (k, v) => k === 'age' ? v + 1 : v);

    let age = jsonObj.age;
    console.log(`年齢： ${age}`);
    ```