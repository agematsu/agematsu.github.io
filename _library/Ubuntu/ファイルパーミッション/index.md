# ファイルパーミッション
ファイルやディレクトリのパーミッションは、NautilusなどのGUIソフトや`ls -l`コマンドで見ることができます。

試しに、geditで`test`ファイルを作って確認してみると、以下のように表示されます。

```
$ ls -l test
-rw-r--r-- 1 username groupname 0  8月 20 16:15 test
```
表示結果の説明は、以下の表になります。

|値|説明|
|:--|:--|
|-|-はファイル、dはディレクトリであることを表す|
|rw-|ユーザーのファイルパーミッション|
|r--|グループのファイルパーミッション|
|r--|その他のファイルパーミッション|
|1|ファイルへのハードリンク？の数|
|username|オーナー名|
|groupname|グループ名|
|0|ファイルのサイズ|

## ファイルのオーナーシップ
すべてのファイルには、ユーザーオーナーとグループオーナーが存在します。

|オーナーシップ|説明|
|:--|:--|
|ユーザー||
|グループ||
|その他||

## ファイルパーミッション

|ファイルパーミッション|ファイルにおいて|ディレクトリにおいて|
|:--|:--|:--|
|r (read)|ファイルを開いたり、読んだりする権利を与えます。|ディレクトリの中身を見る権利を与えます。|
|w (write)|ファイルのコンテンツを変える権利を与えます。|
|e (execute)||

### ８進数での表記
ファイルパーミッションを８進数で表記する方法も、よく使われます。

|数値|パーミッション|
|:--|:--|
|0|---|
|1|--x|
|2|-w-|
|3|-wx|
|4|r--|
|5|r-x|
|6|rw-|
|7|rwx|


<!--
## ファイルマネージャーでの取扱い
### ファイルの場合
ファイルにおいて、プログラムとして実行可能かどうかはチェックポックスで一括して設定できる。
Read-only=r--  
Read and write=rw-  
None=---
### フォルダーの場合
List files only=r--  
Access files=r-x  
Create and delete files=rwx  
None=---
-->


## デフォルトでの設定
Ubuntuで、デフォルトのファイルパーミッションを設定するにはumaskコマンドを使います。  
試しに、ターミナルでumaskと入力すると、次のように現在のumask値が表示されます。

今現在、私のumask値は0044になっていることが分かります。

デフォルトでは、umaskの値は044になっています。しかし、GNOMEのソフトでファイルを作るとumaskが022か002のファイルが作成されます。これを解決するためには、ACLs(Access Controle List)というソフトを使う必要があります。

<!--
参考  
044=-rw--w--w-, drwx-wx-wx  
022=-rw-r--r--, drwxr-xr-x   gedit  
002=-rw-rw-r--, drwxrwxr-x   nautilus, others
-->

## ACLsの使い方
### ACLsの初期設定  

<!--
```
sudo apt-get install acl
```
ただし、デスクトップ版のUbuntuには初めからACLがインストールされているようです。  
インストールされているかは、`sudo dpkg -l`コマンドで確かめられます。
-->
### `getfacl`コマンド  
ファイルの**acls**を読み込むには`getfacl`コマンドを使います。  
試しに`test`ファイルで試してみると、次のようになります。 （ACLsを何も設定してないとこのように表示されます。） 
```
$ getfacl test
# file: test
# owner: username
# group: groupname
user::rw-
group::r--
other::r--
```
### `setfacl -m`コマンド
ファイルの**acls**を変更するには`setfacl -m`コマンドを使います。 
試しに`test`ファイルで試してみると、次のようになります。 
```
$ setfacl -m u:username:rw test && getfacl test
# file: test
# owner: username
# group: groupname
user::rw-
user:rnd:rw-
group::rw-
mask::rw-
other::r--
```
### `setfacl -x`コマンド


<!--
## 外部ストレージのファイルパーミッション~~
-->

## 参考文献
[File Permissions in Linux/Unix with Example](https://www.guru99.com/file-permissions.html)  
[Set the default permissions for newly created files](https://geek-university.com/linux/set-the-default-permissions-for-newly-created-files/)  
[How to set `umask` for the entire gnome session?](https://unix.stackexchange.com/questions/254378/how-to-set-umask-for-the-entire-gnome-session)  
[FilePermissions](https://help.ubuntu.com/community/FilePermissions)  
[How to manage ACLs on Linux](https://linuxconfig.org/how-to-manage-acls-on-linux)  
[Chapter 3. access control lists](http://linux-training.be/storage/ch03.html)
[](https://www.jtp.co.jp/techport/2016-03-02-001/)
