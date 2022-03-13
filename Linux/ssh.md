# Use SSH on Rocky Linux
Rocky Linuxでsshを使用する際の手順について説明します。

Rocky LinuxはCentOS8と同じく初期でSSHがインストールされています。
なのでデーモンを起動する事でssh接続が可能になります。

## SSHの起動と停止
SSHのデーモン起動は下記のコマンドを実行すれば起動します。
`systemctl start sshd`

このままではパソコンを再起動した際にsshdがstopしたままなので、
下記のコマンドで自動起動をオンにします。
`systemctl enable sshd`

sshdを使わない場合はセキュリティ面で危険なので下記のコマンドでオフにします。
`systemctl disable sshd`

## ルートユーザーのアクセスを禁止にする
sshの初期設定だとルートユーザーでのアクセスを許可になっているのですが、
セキュリティ上宜しくないので禁止に変更します。

sshの設定ファイルを編集します。
ファイルパスは下記のフォルダになってます。
`/etc/ssh/sshd_config`
sshd_configの中から`PermitRootLogin`が記述されている行を検索します。

vimの機能を使用した検索方法
ノーマルモードで下記の内容を入力しエンターを押すと検索できます。
`/PermitRootLogin`

見つけたら`PermitRootLogin yes`をコメントアウトし、
その下に`PermitRootLogin no`を追記します。

例
```
#PermitRootLogin yes
PermitRootLogin no
```

完了したら`:wq`を入力して編集を終了できます。
編集が完了したら下記コマンドを実行し、設定ファイルを読み込みましょう。
`systemctl restart sshd`

正しく変更できている場合、ルートユーザーでログインできなくなっています。
もし、ログインできてしまった場合は設定ファイルの編集ミスか設定ファイルの再読み込みができていない可能性があるので確認して下さい。

以上で「Rocky Linuxでsshを使用する手順」終了です、お疲れさまでした。