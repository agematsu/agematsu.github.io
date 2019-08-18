# ファイルパーミッション
Ubuntuにおけるファイルパーミッションの仕組みが分かりにくいので、まとめてみる。
## ファイルのオーナーシップ
Linuxにおけるファイルのオーナーシップは以下の３タイプに分けられる。
### ユーザー

### グループ

### その他

## ファイルパーミッション
### Read
Readパーミッションはファイルを開いたり、読んだりする権利を与えます。
### Write
Writeパーミッションは、ファイルのコンテンツを変える権利を与えます。ディレクトリにおけるWriteパーミッション
### Execute

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
1.ACLsをダウンロードする
```
sudo apt-get install acl
```
## ~~外部ストレージのファイルパーミッション~~

## 参考文献
[File Permissions in Linux/Unix with Example](https://www.guru99.com/file-permissions.html)  
[Set the default permissions for newly created files](https://geek-university.com/linux/set-the-default-permissions-for-newly-created-files/)  
[How to set `umask` for the entire gnome session?](https://unix.stackexchange.com/questions/254378/how-to-set-umask-for-the-entire-gnome-session)  
[FilePermissions](https://help.ubuntu.com/community/FilePermissions)
