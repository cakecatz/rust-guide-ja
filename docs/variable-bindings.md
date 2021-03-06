# 変数の割り当て

最初の項目は変数の割り当てについてです。これを見てください。  

    fn main() {
        let x = 5;
    }

`fn main() {`からいちいち書くのは面倒なので、次からは省略します。  
これからのコードは`main()`関数の中を編集しているということです。  
`main()`を削除するとエラーが出てしまうので気をつけてください。  


多くの言語では、よく変数と呼ばれています。しかし、Rustの変数割り当てはいくつかの技があります。  
Rustはとても強力な`パターンマッチング`と呼ばれる機能を持っています。この機能についてはその内詳しく話しますが、  
左側の`let`式は完全なパターンで、変数の名前を表すだけではないです。  
つまり、次のような事もできるということです。  

      let (x, y) = (1, 2);  

この式が実行されると、`x`が１になり`y`が２になります。 **パターン** は本当にパワフルです。  
しかし、これについて話すのは今はやめて、このまま進みましょう。  

Rustは静的型付け言語です。これは、変数の型を予め指定するということを意味しています。  
それではなぜ最初の例はコンパイルできたのでしょうか？  
はい、これはRustが`型推論`を持っているからです。　　
もし何の型なのか推定することができたら、Rustに対して明示的に型を宣言する必要がありません。  

もちろん型をつけることもできます。コロン(`:`)のあとに型名を書きます。  

    let x: i32 = 5;

これをどうやって読むかというと、「`x`を`i32`という型、値は`5`で割り当てます」という感じです。  

これからの例はコメントで注釈をつけることがあります。  
こんな風にです。  

    fn main() {
        let x = 5; // x: i32
    }

この注釈と`let`構文は似ているので注意してください。  
これらのコメントはRustでは慣用的ではないですが、変数の型が何であるのか理解するための助けになると思います。  

変数は通常`イミュータブル(immutable)`です。  
次のコードはコンパイルできません。  

    let x = 5;
    x = 10;

おそらく、このようなエラーが出力されます。  

    error: re-assignment of immutable varitable `x`
         x = 10;
         ^~~~~~~

もしもミュータブルに変数を宣言したいのであれば、`mut`を使うことができます。  

    let mut x = 5; // mut x: i32
    x = 10;

１つの理由からイミュータブルがデフォルトになっているわけではありませんが、  
Rustが **安全性** に焦点をあてていることを、理由の一つとして考えることができます。  
もしも`mut`をつけることを忘れたら、意図しない変更が行われたとコンパイラが教えてくれます。  
初期値がミュータブルだった場合、コンパイラがこのことに気づくことができません。  
ですから、ミュータブルな変数を使いたい場合は、簡単です。`mut`をつけてください。  

他にもミュータブルを避ける理由があるのですが、これはこのガイドが扱う範囲外です。  
一般的に、明示的な変更を避ける事ができるので、Rustではこれを採用しています。  
しかし、たまに変更するこが必要なこともあるので、禁止にはしていないです。  

変数の割り当ての話に戻りましょう。  
Rustの変数の割り当ては他の言語と異なった側面を持っています。  
その変数を使う前に値を入れて初期化する必要があることです。  

実際に試してみましょう。  
`src/main.rs`を次のように変更してください。  

    fn main() {
        let x: i32;

        println!("Hello, world!");
    }

`cargo build`を使ってビルドできます。  
`warning(警告)`が表示されますが、まだ`"Hello, world!"`は表示されるはずです。  

       Compiling hello_world v0.0.1 (file:///home/you/projects/hello_world)
    src/main.rs:2:9: 2:10 warning: unused variable: `x`, #[warn(unused_variable)] on by default
    src/main.rs:2     let x: i32;
                          ^

Rustは割り当てている変数が使用されていないと警告していますが、それを使うことはないので特に問題はありません。  
しかしこの変数を使おうとすると話は変わります。さあ、やってみましょう。  
次のようにプログラムを変更してください。  

    fn main() {
        let x: i32;

        println!("The value of x is: {}", x);
    }

そしてビルドします。  
おそらくエラーが出ます。  

    $ cargo build
       Compiling hello_world v0.0.1 (file:///home/you/projects/hello_world)
    src/main.rs:4:39: 4:40 error: use of possibly uninitialized variable: `x`
    src/main.rs:4     println!("The value of x is: {}", x);
                                                        ^
    note: in expansion of format_args!
    <std macros>:2:23: 2:77 note: expansion site
    <std macros>:1:1 3:2 note: in expansion of println!
    src/main.rs:4:5: 4:42 note:expansion site
    error: aborting due to previous error
    Could not compile `hello_world`.

Rustは初期化されていない値を使用させません。  
次は、`println!`に追加したいくつかのものについて話しましょう。  

もし出力する文字列に２つの波括弧`{}`を加えると、Rustはそこで値の補間がされると解釈します。  
`String interpolation(文字列の補間)`はコンピュータサイエンスの言葉で、  
文字列の間にデータを埋め込むという意味です。コンマを付け、そのあとに`x`を入れると、  
`x`の値を補間したいということを示していることになります。  
コンマは、関数やマクロへひとつ以上の引数を渡す際にも使います。  

あなたが波括弧を使うと、Rustは値の型に合わせて表示を行います。特定の方法で表示したい場合は、  
[幅広いオプションが利用可能です(英)](http://doc.rust-lang.org/std/fmt/)。  
整数を出力するのは簡単なので、今回はデフォルトのまま表示しました。  



