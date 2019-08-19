# Ubuntuのユーザーについて
Ubuntuのユーザーの設定について見ていきます。

## ユーザー
Ubuntuをインストールすると、ます初めにユーザーを作ります。

ユーザーを追加するには、`useradd`コマンドを使います。コマンドラインからユーザーを作ると、一般的にホームディレクトリにフォルダは作られないので、`-m`
オプションを使います。

### ルートユーザー
Ubuntuでは、ルートユーザーは、デフォルトではログインできないようになっている。
おそらく、ルートユーザーはグループの一種だと思う。

## グループ
すべてのユーザーは、少なくとも１つ以上のグループに属します。
グループの一覧は
グループは`id`または`groups`コマンドで調べることができる。

### プライマリーグループとセカンダリーグループ


## sudoコマンド

## Ubuntu Single Sign Onについて
[Ubuntu Single Sign On](https://en.wikipedia.org/wiki/Ubuntu_Single_Sign_On)は改称してUbuntu Oneになったようだ。Ubuntu OneはUbuntuを作っているCanonicalという会社のウェブサイトにログインするためのアカウントのようだ。これをUbuntuに登録するメリットは今のところよく分からない。少なくとも、複数のUbuntu間で同一のユーザーを使うための仕組みではなさそうだ。
## 参考文献
[User management](https://help.ubuntu.com/lts/serverguide/user-management.html#user-profile-security)  
[How to Create Users in Linux (useradd Command)](https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/)
