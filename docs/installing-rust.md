#Rustのインストール  

Rustでプログラミングをするためには、まず、コンパイラをPCにインストールする必要があります。  
Rustコンパイラをインストールする方法はいくつか存在していますが、  
まずは一番簡単な方法を使ってのインストールを行いましょう。`rustup`スクリプトを使用する方法です。  

LinuxかMacを使用している人は、ターミナルで下のコマンドを実行してください  
(`$`はシェルでの入力を表しているだけなので、実際に入力する必要はありません)

    $ curl -L https://static.rust-lang.org/rustup.sh | sudo sh

もし`curl | sudo sh`を使用した[インストール方法が心配だと感じる](http://rcmdnk.github.io/blog/2014/02/24/computer-github/)なら、次の二段階に分ける方法でインストールスクリプトの内容を調べてください。  

    $ curl -L https://static.rust-lang.org/rustup.sh -O
    $ sudo sh rustup.sh  

もしWindowsを使っていたら、[32bit用インストーラー](https://static.rust-lang.org/dist/rust-nightly-i686-pc-windows-gnu.exe)か[64bit用インストーラー](https://static.rust-lang.org/dist/rust-nightly-x86_64-pc-windows-gnu.exe)をダウンロードして実行してください。  

もしあなたがRustを使わないことに決めたら、それは悲しいことですが、しょうがありません。  
どのプログラミング言語もすべての人にとって素晴らしいものとは限らないですからね。  
先ほどのスクリプトに引数を加えて実行してください。  

    curl -s https://static.rust-lang.org/rustup.sh | sudo sh -s -- --uninstall  

もしもWindowsのインストーラーを使用していたら、もう一度`.exe`を実行することで  
アンインストールオプションが表示されるはずです。  

Rustをアップデートしたいときは`rustup`スクリプトを実行してください。  
今の時点では、何度か行うことになるはずです。  
Rustはまだ1.0ではないので、何か行う際には最新版のRustを想定するからです。  

ここから少し重要な話ですが、  
`curl | sudo sh`を使うように指示すると、一部の人はやや当然なんですが非常に怒ります。  
このようなスクリプトを実行する時は、基本的にこのスクリプトを作成したRustのメンテナが良い人物で、  
あなたのPCをハックし、悪いことをしないと信頼している必要があります。  
このような考えを持つのはいいことで、もしあなたもその一人ならば、  
次のドキュメントをチェックしてください。  

[ソースからRustをビルド(英)](https://github.com/rust-lang/rust#building-from-source)  
[公式バイナリダウンロード(英)](http://www.rust-lang.org/install.html)  

ここで公式にサポートしているプラットフォームを記載しておきます。  

- Windows (7, 8, Server 2008 R2)
- Linux (2.6.18 or later, various distributions), x86 and x86-64
- OSX 10.7 (Lion) or greater, x86 and x86-64  

Rustはこれらのプラットフォームに加えていくつかの環境、  
例えばAndroid等で広範囲にテストを行っています。  

しかし、上記のプラットフォームがはほとんどのテストを行っているため、  
もっとも安定して動作するでしょう。  

最後に、Windowsに対して少し言及します。  
Rustは、Windowsがリリースをする際のファーストクラス-プラットフォームであるべきと考えていますが、
正直に言うと、Windowsでの体験はLinux/OS Xと比べるとまだ完全なものではありません。  
私達はそれに取り組んでいます！もし何かきちんと動かなかった場合は、おそらくバグです。  
何か起きたら私達に教えてください。それぞれ、すべてのコミットは他のプラットフォーム同様、  
Windowsでもテストされています。

Rustがきちんとインストールされたら、シェルを立ち上げ次のコマンドを実行してみてください。  

    $ rustc --version

するとこのような出力が確認できるはずです。  

    rustc 1.0.0-nightly (d3732a12e 2015-02-06 23:30:17 +0000)

表示されましたか？  
もし同じように表示されていたら、Rustのインストールは完了です!!  

うまくいかない場合は、[Stack Overflow](https://ja.stackoverflow.com/questions/tagged/rust)が助けになると思います。  
もしくは、**#rustlang** をつけてTwitterでつぶやいてください。