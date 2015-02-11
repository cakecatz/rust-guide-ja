#Rustのインストール  

Rustでプログラミングをするためには、まず、コンパイラをPCにインストールする必要があります。
Rustコンパイラをインストールする方法はいくつか存在していますが、まずは一番簡単な方法を使ってのインストールを行いましょう。`rustup`スクリプトを使用する方法です。  
LinuxかMacを使用している人は、ターミナルで下のコマンドを実行してください(`$`はターミナルでの入力を表しているだけなので、実際に入力する必要はありません)：

    $ curl -L https://static.rust-lang.org/rustup.sh | sudo sh

もし`curl | sudo sh`を使用した[インストール方法が心配だと感じる](http://rcmdnk.github.io/blog/2014/02/24/computer-github/)なら、次の二段階に分ける方法でインストールスクリプトの内容を調べてください。  

    $ curl -L https://static.rust-lang.org/rustup.sh -O
    $ sudo sh rustup.sh  

もしWindowsを使っていたら、[32bit用インストーラー](https://static.rust-lang.org/dist/rust-nightly-i686-pc-windows-gnu.exe)か[64bit用インストーラー](https://static.rust-lang.org/dist/rust-nightly-x86_64-pc-windows-gnu.exe)をダウンロードして実行してください。  

もしあなたがRustを使わないことに決めたら、それは悲しいことですが、しょうがありません。  
どのプログラミング言語もすべての人にとって素晴らしいものとは限らないですからね。  
先ほどのスクリプトに引数を加えて実行してください。  

    curl -s https://static.rust-lang.org/rustup.sh | sudo sh -s -- --uninstall  


