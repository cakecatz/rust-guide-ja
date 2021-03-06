# Hello,world!

すでにRustがインストールされていると思うので、最初のRustプログラムを作りましょう。  
新しい言語での初めてのプログラミングと言えば、'Hello,World!'とスクリーンに表示するプログラムです。  

簡単なプログラムから始めるのは、コンパイラが正しくインストールされていて、  
きちんと動くことを確認することができるので、いいことです。  
また、スクリーンに情報を表示することは何をするにしても必要です。  

プログラミングをするにあたって必要ことは、コードを書くファイルを作成することです。  
私は自分のホームディレクトリに`projects`というフォルダを作り、  
そこにすべてのプロジェクトを入れますが、コードはどこに置いていようがRustは気にしません。  

これは実際には私達が取り組むべき一つの問題になるのですが、  
このガイドはコマンドラインの知識を持っていることを前提に作成しています。  
Rustを使うにあたって、コマンドラインに対する大量の知識を持つ必要はないのですが、  
言語が完成するまでは、IDEサポートはまだまだの状態です。  
Rustでのプログラミングには特定のエディタを指定はしません。コードの置き場所もです。  

ということで、プロジェクト用のディレクトリを作成しましょう！  

    $ mkdir ~/projects
    $ cd ~/projects
    $ mkdir hello_world
    $ cd hello_world

もしOSがWindowsで、PowerShellを使っていなかったら、`~`は使えません。  
詳しくはあなたの使用しているシェルのドキュメントを見てください。  

それでは次に、新しいソースファイルを作りましょう。この例では`editor filename`という構文を、  
`filename`というファイルを編集するという意味で使用しますが、あなたの好きなもの使って構いません。  

作成するファイルは`main.rs`という名前にしましょう。  

    $ editor main.rs

Rustのファイルは常に`.rs`という拡張子で終わります。もしファイルの名前にひとつ以上の英単語を使用したいのであれば、  
アンダースコアを使ってください。`helloworld.rs`ではなく`hello_world.rs`のようにです。  


ファイルを開いて、次のコードを入力してください。  

    fn main() {
        println!("Hello, World!");
    }

ファイルを保存して、次のコマンドをターミナルに打ち込みましょう！  

    $ rustc main.rs
    $ ./main # Windowsの場合は main.exeです
    Hello, world!

[play.rust-lang.org](https://play.rust-lang.org/)でサンプルプログラムを実行することができます。  
左上にある`evaluate`というボタンを押すことでプログラムが実行されます。  


うまくいきましたね！  
それでは何が起きたのか少しづつ見て行きましょう。  

    fn main() {

    }

上の数行はRustでの *function* (関数)の宣言です。`main`関数は特殊で、  
Rustのプログラムの一番最初に実行される場所になっています。  
最初の行は、「私は **main** という名前の関数を宣言します。引数も戻り値もありません。」という意味です。  
もし引数をとりたければ、丸括弧`(`と`)`の間に書きます。  
それに加え、この関数は何の値も返さないので戻り値の型を省略することができます。  
このあたりについては後々学んでいきましょう。  

また、関数が`{`と`}`で囲まれていることにも注意してください。Rustでは関数の本体を`{}`を使って囲む必要があります。  
最初の括弧は関数の宣言と同じ行にするのが良いでしょう。間には1つスペースを入れてください。  

次はこの行ですね。  

          println!("Hello, world!");

この行が作成したプログラムが行っていることのすべてになります。  
ここでは重要な点がいくつかあります。１つ目は、インデントが４つの空白ということです。TABではないです。  
あなたのエディタの設定を、TABキーを押したら４つの空白を挿入するように設定してください。  

２つ目は`println!()`の部分です。これはRustの *macro* を呼び出しています。  
**マクロ** はRustでメタプログラミングを行うためのものです。もしも代わりに関数を使うのであれば、  
`println()`というようにします。今回はこの２つの違いについて気にする必要はありません。  
覚えて欲しいのは`!`があったら、それは通常の関数の代わりにマクロを呼び出しているということです。  
Rustはある利点から関数ではなくマクロの`println!`を実装していますが、とても高度な話題になります。  
マクロについてはもっと後で解説する時に学んでいきましょう。  
最後に言及しておきますが、もしあなたがC言語でマクロを使ったことがあったとしても、  
Rustのマクロとはかなり異なっています。  
とにかく、マクロを使うことは恐れないでください。  
これから少しづつ学んでいくので、今は信じてついて来てください。  

次の`"Hello, world!"`、これは文字列です。  
文字列というのはシステムプログラミング言語ではとても複雑なトピックです。  
この文字列は **静的に割り当てられた** 文字列です。割り当ての種類と違いについては後で解説します。  

私達は`println!`の引数に文字列を渡し、スクリーンにその文字列を出力します。  
とっても簡単ですね！  


最後ですが、行はセミコロン(`;`)で終わります。Rustは式指向言語で、すべてを式として扱います。  
`;`は式の終わりを表していて、次の式の準備が始まります。  
ほとんどのRustのコードの行末は`;`になっています。  
後々このガイドでこのことについてもカバーしていきます。  


そして、実際にコンパイルしてプログラムを実行しています。  
Rustのコンパイラ、`rustc`にソースファイルを渡すことでコンパイルすることができます。  

    $ rustc main.rs

もしCやC++を知っていたなら、これは`gcc`や`clang`に似ていると思ったでしょう。  
Rustは実行形式のバイナリを出力します。`ls`コマンドで確認することができます。  

    $ ls
    main main.rs

Windowsの場合なら、こうです。  

    $ dir
    main.exe main.rs

いま２つのファイルが存在してますね。  
`.rs`拡張子から始まるソースコードファイルと実行ファイルです。(Windowsでは`main.exe`で、それ以外は`main`です)  

    $ ./main # Windowsなら main.exe です

これは`Hello, world!`をターミナルに出力します。  

もしあなたが **Ruby**や**Python**、**JavaScript** のように動的な言語から来たのなら、  
おそらくこのような二段階に分離している作業に慣れていないでしょう。  
Rustは **事前コンパイル言語** です。  
つまり、コンパイルしたプログラムは、実行する際にRustがインストールされている必要がないということです。  
もしあなたが、他の誰かに`.rb`や`.py`、`.js`ファイルを渡したら、  
それらを実行するためにはRuby/Python/JavaScriptがインストールされていなければなりません。  
しかし、一度のコマンドでコンパイルと実行をすることができます。  
すべては言語設計によるトレードオフで、Rustはこの選択をしたということです。  

おめでとう:clap:  
あなたは公式なRustプログラムを書きましたよ。  
これであなたはRustプログラマーです!  
ようこそ!  

次はCargoというツールを紹介したいと思います。これは実際にRustのプログラムを書く時に使われています。  
`rustc`のみを使うのもシンプルで素敵ですが、あなたのプロジェクトは成長していくので、  
すべてのオプションの管理しやすくするために、そしてプロジェクトを他の人々と共有するための助けが欲しくなるはずです。

