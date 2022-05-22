# sudoersとは

- sudoersとはなんぞ？
  - sudoコマンドを使用できるユーザーと権限を設定する為のファイルです。

- sudoとは
  - 管理者権限でコマンドを実行したい時に使用するコマンドです。

# Sudoersにsudo権限を付与する

## ユーザー切り替え
`sudoers`は`/etc/sudoers`に記述されている。<br>
`sudoers`はroot権限でしか扱えない為、rootユーザーに切り替える必要があるので下記のコマンドを実行<br>
```
su - #rootユーザーに切り替える
```

## sudoersファイル編集

rootユーザーに切り替えたら下記コマンドを実行<br>
```
visudo
```
記述する位置はどこでもいいが、ファイル末尾か`%wheel  ALL=(ALL)       ALL`の下に記述する。<br>

下記の内容を記述すれば完了
```
sudo認可したいユーザー名 ALL=(ALL) ALL
```

## sudoersの構文

```
sudo認可したいユーザー名 ALL=(ALL) ALL
```
|sudo認可したいユーザー名 |ALL= |(ALL) |ALL|
|---|---|---|---|
|どのユーザーが|すべてのホストで|すべてのユーザーに変身でき|すべてのコマンドを実行できる|

全てのユーザーに権限を付与したい場合は下記の内容を記述すれば適用されます。（非推奨）<br>

```
root ALL=(ALL) ALL
```

---

編集が完了したら`:wq`で上書き保存して終了。<br>
上書きして閉じたら、実行したいユーザーに切り替え適用されているか確認して終了です。

# 参考
- [RedHat 基本的なシステム設定の構成 - 第23章 sudo アクセスの管理](https://access.redhat.com/documentation/ja-jp/red_hat_enterprise_linux/8/html/configuring_basic_system_settings/managing-sudo-access_configuring-basic-system-settings)
- [man - SUDOERS](https://linuxjm.osdn.jp/html/sudo/man5/sudoers.5.html)
- [maruko2 Note - 一般ユーザーを sudo できるようにする](http://www.maruko2.com/mw/%E4%B8%80%E8%88%AC%E3%83%A6%E3%83%BC%E3%82%B6%E3%83%BC%E3%82%92_sudo_%E3%81%A7%E3%81%8D%E3%82%8B%E3%82%88%E3%81%86%E3%81%AB%E3%81%99%E3%82%8B)
