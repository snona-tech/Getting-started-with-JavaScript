## HTTPとは

HTTPはサーバとHTMLなどのデータをやり取りするための通信プロトコルの一つ。<br>
最近ではHTMLを直接データでやり取りするのではなく、必要なデータのみをJSON形式でやり取りし、クライアント側のJavaScriptでデータを加工してHTMLを生成/表示するることが多い。

!!! tip "JSON形式"

    共通のデータ記述形式の一つ。key:value形式で定義される。

    JSONの例

    ```json
    {
        "id": 1,
        "name": "ジャバ　スクリプト",
        "age": 25,
        "hobby": [ "スカッシュ", "料理", "テレビドラマ" ]
    }
    ```

## HTTPリクエスト

クライアントからサーバにHTTP通信でアクセスすることをHTTPリクエストという。

### リクエストの構成

HTTPリクエストは主に以下の構成でサーバに送信される。

#### リクエストヘッダ

* URL：サーバのURL
* HTTPメソッド：いくつか種類があり、それぞれ用途がある。（以下は代表的なメソッド）
    * GET<br>
      データの一覧取得やキーワード検索などに用いられる。<br>
      検索キーワードなどは基本的にURLパラメータを利用する。<br>
      例）`GET /api/search?keyword=キーワード`
    * POST<br>
      データの登録やログインなどに用いられる。<br>
      登録情報などのデータはJSONなどでリクエストボディとしてサーバに送る。
    * PUT<br>
      データの更新などに用いられる。
    * DELETE<br>
      データの削除などに用いられる。
* Cookie：クッキーに保存されているセッション情報など

#### リクエストボディ（インプットペイロード）

JSON形式などでユーザがフォーム入力した情報など。<br>
POST、PUT、DELETEメソッドなどで利用される。

## HTTPレスポンス

クライアントからサーバにHTTP通信でアクセスした際に、サーバから返却される応答のことをHTTPレスポンスという。

### レスポンスの構成

HTTPレスポンスは主に以下の構成でクライアントに送信される。

#### レスポンスヘッダ

* HTTPステータスコード[^1]
  * コードの値によってリクエストの成功失敗が判断できる。<br>
    例えば、200番台であれば成功であり、`200(OK)`はリクエスト成功を意味する。<br>
    他にも、`404(Not Found)`はリクエスト先が見つからなかったことを意味する。

[^1]: 多くのコードが用意されており、それぞれ意味が決まっている。実際にコードを設定して返却するのはサーバ側。<br>詳細は「[HTTP レスポンスステータスコード](https://developer.mozilla.org/ja/docs/Web/HTTP/Status)」を参照。

#### レスポンスボディ（アウトプットペイロード）

検索結果やアカウント情報など、リクエストに応じたデータが返却される。<br>
返却されるレスポンスの形式はサーバによって異なる。

## AJAX

Asynchronous JavaScript and XML の頭文字をとったものであり、サーバとHTTP通信する際に必要な技術を組み合わせたアプローチのこと。

!!! note "構文"

    ```javascript
    // XMLHttpRequestオブジェクトの初期化
    let http = new XMLHttpRequest();

    /*
    XMLHttpRequestオブジェクトの設定
    ・リクエスト先とメソッドの設定
    ・リクエストヘッダの設定
    ・リクエスト送信後の応答結果の処理設定
    ・HTTP通信エラー時の処理設定
    */
    http.open(メソッド, URL);
    http.setRequestHeader(ヘッダ名, ヘッダの値);
    http.onload = () => {
        if (http.status === 200) {
            /*
            ステータスコードが200(リクエスト成功)の場合の処理
            レスポンスデータは http.response で取得できる
            */
        } else {
            // ステータスコードが200以外の場合の処理
        }
    };
    http.onerror = () => {
        // HTTP通信エラー時の処理
    };

    // HTTPリクエスト送信
    http.send();
    ```

!!! example "使用例"

    [ZIPCODA](https://zipcoda.net/) が提供している郵便番号検索APIを利用し、郵便番号から住所を検索する。<br>
    [ZIPCODA](https://zipcoda.net/) にアクセスした上で開発者ツールを開き[^2]、コンソールに以下を入力して実行する。<br>

    [^2]: セキュリティの都合上、別のサイトのコンソールを通じてJavaScriptからアクセスできないようになっている。

    ```javascript
    let http = new XMLHttpRequest();
    http.open('GET', 'https://zipcoda.net/api?zipcode=2410821');
    http.onload = () => {
        if (http.status === 200) {
            console.log("成功");
            console.log(http.response);
        } else {
            console.log("エラーが発生しました。");
            console.log(http.response);
        }
    };
    http.onerror = () => console.log("予期せぬエラーが発生しました。");
    http.send();
    ```
