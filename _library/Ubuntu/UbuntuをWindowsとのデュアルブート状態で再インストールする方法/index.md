UbuntuをWindowsとデュアルブートしている状態で、Ubuntuを再インストールする方法を見ていきます。
## Step 1.
まずは、再インストールするためのLive USBを準備します。
## Step 2.
Biosの設定で、ブートの順番をUSBからにして、Live USBを差し込んだ状態で、再起動します。
## Step 3.
Live USBからブートした後は、インストーラを起動して、設定を進めていきます。Installion type画面になったところで、Something elseを選択してください。

<p align="center">
 <img width="350" height="250" src="install option fixed.jpg">
</p>

## Step 4.
いよいよパーテーションを設定する画面になります。はじめに、Ubuntuがインストールされているドライブを確認しましょう。私の場合は、/dev/nvme0n1p6にインストールされていることが確認できます。そうすると、Ubuntuがインストールされているパーテーションを選択してマイナスアイコンをクリックすると、そのパーテーションがfree spaceになります。

<p align="center">
 <img width="350" height="250" src="install partition fixed.jpg">
</p>

<!--
このときに、Ubuntuがくらも２つに分かれていることが有ります
-->

## Step 5.
free spaceにrootディレクトリとhomeディレクトリを作っていきます。先程作った、free spaceを選択してプラスアイコンを押し...

## 参考文献 
[How to Replace One Linux Distribution With Another From Dual Boot [Keeping Home Partition]](https://itsfoss.com/replace-linux-from-dual-boot/) 
