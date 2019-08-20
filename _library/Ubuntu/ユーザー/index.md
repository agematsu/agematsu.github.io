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
グループの一覧は、`cat /etc/group`コマンドで確認できます。
ためしに`head /etc/group`コマンドで、最初だけ表示してみると次のようになります。
```
$ head /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:syslog
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
```
ここで、xはパスワードの置き場所であることを表しています。  
以前はグループパスワードは/etc/groupファイルに置かれていましたが、セキュリティの問題で/group/shadowファイルに移されました。 

現在のユーザーのグループは`id`または`groups`コマンドで調べることができます。
### グループの目的

### プライマリーグループとセカンダリーグループ
`id`,`groups`などのコマンドを入力したときに最初にに表示されるグループをプライマリーグループ、それ以外のグルーブをセカンダリーグループといいます。
## sudoコマンド

## Ubuntu Single Sign Onについて
[Ubuntu Single Sign On](https://en.wikipedia.org/wiki/Ubuntu_Single_Sign_On)は改称してUbuntu Oneになったようだ。Ubuntu OneはUbuntuを作っているCanonicalという会社のウェブサイトにログインするためのアカウントのようだ。これをUbuntuに登録するメリットは今のところよく分からない。少なくとも、複数のUbuntu間で同一のユーザーを使うための仕組みではなさそうだ。
## 参考文献
[User management](https://help.ubuntu.com/lts/serverguide/user-management.html#user-profile-security)  
[How to Create Users in Linux (useradd Command)](https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/)  
[Managing Group Accounts in Ubuntu](http://www.pearsonitcertification.com/articles/article.aspx?p=2931570)
