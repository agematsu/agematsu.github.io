# ACLsの使い方
## ACLsの初期設定
書きかけ
<!--
```
sudo apt-get install acl
```
ただし、デスクトップ版のUbuntuには初めからACLがインストールされているようです。  
インストールされているかは、`sudo dpkg -l`コマンドで確かめられます。
-->
## `getfacl`コマンド  
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
## `setfacl -m`コマンド
ファイルの**acls**を変更するには`setfacl -m`コマンドを使います。  
試しに`test`ファイルで試してみると、次のようになります。 
```
$ setfacl -m u:username:rw test && getfacl test
# file: test
# owner: username
# group: groupname
user::rw-
user:username:rw-
group::rw-
mask::rw-
other::r--
```
## mask
## `setfacl -x`コマンド
## `setfacl -d`コマンド
ディレクトリに
```
~$ setfacl -d -m o:rw test && getfacl test
# file: test
# owner: username
# group: groupname
user::rwx
group::rwx
other::r-x
default:user::rwx
default:group::rwx
default:other::rw-
```

## 参考文献 
[How to set `umask` for the entire gnome session?](https://unix.stackexchange.com/questions/254378/how-to-set-umask-for-the-entire-gnome-session)  
[FilePermissions](https://help.ubuntu.com/community/FilePermissions)  
[How to manage ACLs on Linux](https://linuxconfig.org/how-to-manage-acls-on-linux)  
[Chapter 3. access control lists](http://linux-training.be/storage/ch03.html)
[](https://www.jtp.co.jp/techport/2016-03-02-001/)
