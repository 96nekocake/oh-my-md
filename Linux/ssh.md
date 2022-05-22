# Rocky Linux（Red Hat系）でsshdを起動する

- sshdとはなんぞ？
  -  sshで接続する時に使用されるデーモンプログラム
- sshとは？
  - リモートでサーバーにログインできるようにする仕組みである

# SSHの起動と停止
Rocky LinuxはCentOS8と同じく初期でsshdがインストールされているので、デーモンを起動するだけでssh接続が可能です。<br>

sshdの起動は下記のコマンドを実行すれば起動します。<br>
`systemctl start sshd`

このままではパソコンを再起動した際にsshdが停止したままなので、毎回起動するのが面倒な人は下記のコマンドで自動起動をオンに変更しましょう<br>
`systemctl enable sshd`

sshdを使わない場合はセキュリティ面で危険なので下記のコマンドでオフに変更しましょう。
`systemctl disable sshd`

# SSH経由のルートユーザーユーザーログインを無効にする
sshの初期設定だとルートユーザーでのアクセスが有効化されており、セキュリティ的に宜しくないので無効化します。<br>

## sshdのコンフィグを編集
sshの設定ファイルを編集します。<br>
コンフィグは下記の場所にあります。<br>
`/etc/ssh/sshd_config`<br>
vimを使うなら下記コマンドをコピペで編集可能。<br>
`vim /etc/ssh/sshd_config`
sshd_configの中から`PermitRootLogin`が記述されている行を検索<br>
見つけたら`PermitRootLogin yes`をコメントアウトし、その下に`PermitRootLogin no`を追記<br>

例
```config:sshd_config
#PermitRootLogin yes
PermitRootLogin no
```

完了したら`:wq`を入力して編集を終了できます。<br>
編集が完了したら下記コマンドを実行し、sshdを再起動<br>
`systemctl restart sshd`

正しく変更できている場合、ルートユーザーでログインできなくなっています。<br>
もし、ログインできてしまった場合は設定ファイルの編集ミスか設定ファイルの再読み込みができていない可能性があるので確認して下さい。<br>

# 参考
- [RedHat システム管理者のガイド - 第12章 OpenSSH](https://access.redhat.com/documentation/ja-jp/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-openssh)
- [RedHat システム管理者のガイド - 12.2. OpenSSH の設定](https://access.redhat.com/documentation/ja-jp/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-openssh)
- [manページ - SSHD](https://nxmnpg.lemoda.net/ja/8/sshd)
