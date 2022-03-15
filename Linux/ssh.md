# Use SSH on Rocky Linux
Rocky Linuxでsshを使用する際の手順について説明します。<br>

Rocky LinuxはCentOS8と同じく初期でSSHがインストールされています。<br>
なのでデーモンを起動する事でssh接続が可能になります。

## SSHの起動と停止
SSHのデーモン起動は下記のコマンドを実行すれば起動します。<br>
`systemctl start sshd`

このままではパソコンを再起動した際にsshdがstopしたままなので、
下記のコマンドで自動起動をオンにします。<br>
`systemctl enable sshd`

sshdを使わない場合はセキュリティ面で危険なので下記のコマンドでオフにします。<br>
`systemctl disable sshd`

## ルートユーザーのアクセスを禁止にする
sshの初期設定だとルートユーザーでのアクセスを許可になっているのですが、
セキュリティ上宜しくないので禁止に変更します。<br>

sshの設定ファイルを編集します。<br>
ファイルパスは下記のフォルダになってます。<br>
`/etc/ssh/sshd_config`
sshd_configの中から`PermitRootLogin`が記述されている行を検索します。<br>

vimの機能を使用した検索方法
ノーマルモードで下記の内容を入力しエンターを押すと検索できます。<br>
`/PermitRootLogin`

見つけたら`PermitRootLogin yes`をコメントアウトし、
その下に`PermitRootLogin no`を追記します。<br>

例
```
#PermitRootLogin yes
PermitRootLogin no
```

完了したら`:wq`を入力して編集を終了できます。<br>
編集が完了したら下記コマンドを実行し、設定ファイルを読み込みましょう。<br>
`systemctl restart sshd`

正しく変更できている場合、ルートユーザーでログインできなくなっています。<br>
もし、ログインできてしまった場合は設定ファイルの編集ミスか設定ファイルの再読み込みができていない可能性があるので確認して下さい。<br>

以上で「Rocky Linuxでsshを使用する手順」終了です、お疲れさまでした。
