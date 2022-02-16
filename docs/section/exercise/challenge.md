## FizzBuzz問題

プログラミング能力があるかどうかを見極める手法として提唱された問題。<br>
意外にも現役のエンジニアでも正解できなかったりする。

!!! note "FizzBuzz問題"

    1から100までの数字を表示するプログラムを作成する。<br>
    ただし、以下の条件で出力内容を変えること。

    * 3の倍数の場合は`Fizz`
    * 5の倍数の場合は`Buzz`
    * 15の倍数の場合は`FizzBuzz`

!!! question "問題 1-1：FizzBuzz問題（コンソール版）"

    FizzBuzz問題を開発者ツールのコンソールで解きなさい。

!!! question "問題 1-2：FizzBuzz問題（Webサイト版）"

    1からNまでの数を表示するFizzBuzz問題のWebサイトを作成しなさい。<br>
    ただし、Nはユーザが画面から入力できるようにし、実行ボタン押下で数字が表示されるようにしなさい。<br>
    また、Nは1から100までの数値とし、それ以外の入力についてはユーザにエラーメッセージを出力すること。

## 郵便番号検索

!!! question "問題 2-1：郵便番号検索サイト"

    郵便番号から住所を検索するWebサイトを作成しなさい。<br>
    郵便番号はユーザが入力できるようにし、検索ボタン押下で住所が表示されるようにしなさい。<br>
    郵便番号の検索には以下のAPIを使用すること。

    * ZIPCODA API：https://zipcoda.net/doc

    また、該当する住所が存在しない場合もハンドリングし、ユーザにエラーメッセージを表示しなさい。

## 電卓アプリ

!!! question "問題 3-1：電卓アプリのUI"

    電卓アプリの画面をHTMLとCSSで作成しなさい。

    <figure markdown>
        ![電卓アプリの画面イメージ](../../assets/images/calc.drawio.svg){ width="auto" }
        <figcaption>電卓アプリの画面イメージ</figcaption>
    </figure>

    ??? hint "ヒント"

        [Bootstrap](https://getbootstrap.jp/) などのCSSフレームワークを利用するとより効率的に画面デザインが行える。

!!! question "問題 3-2：電卓アプリの計算処理"

    電卓アプリの計算処理をJavaScriptで作成し、画面と合わせて電卓アプリを完成させなさい。

    ??? hint "ヒント"

        JavaScriptには、文字列をそのままJavaScriptのプログラムとして解釈し、実行する`eval`関数がある。<br>
        詳細は「[eval()](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/eval)」を参照。

        ただし、上記サイトにも記載がある通り、`eval`関数は**^^非推奨のため実際の業務では使用しない^^**こと。
