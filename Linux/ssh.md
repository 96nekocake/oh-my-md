# Use SSH on Rocky Linux
Rocky Linuxでsshを使用する際の手順について説明します。<br>

<!-- more -->

Rocky LinuxはCentOS8と同じく初期でSSHがインストールされているので、デーモンを起動するだけでssh接続が可能になります。

## SSHの起動と停止
SSHのデーモン起動は下記のコマンドを実行すれば起動します。<br>
`systemctl start sshd`

このままではパソコンを再起動した際にsshdがstopしたままなので、下記のコマンドで自動起動をオンに変更<br>
`systemctl enable sshd`

sshdを使わない場合はセキュリティ面で危険なので下記のコマンドでオフに変更しましょう。<br>
`systemctl disable sshd`

## ルートユーザーのアクセスを禁止にする
sshの初期設定だとルートユーザーでのアクセスを許可になっているのですが、セキュリティ上宜しくないので禁止に変更します。<br>

sshの設定ファイルを編集します。<br>
コンフィグは下記の場所にあります。<br>
`/etc/ssh/sshd_config`<br>
vimを使うなら下記コマンドをコピペで編集可能。<br>
`vim /etc/ssh/sshd_config`
sshd_configの中から`PermitRootLogin`が記述されている行を検索<br>
見つけたら`PermitRootLogin yes`をコメントアウトし、その下に`PermitRootLogin no`を追記<br>

例
```
#PermitRootLogin yes
PermitRootLogin no
```

完了したら`:wq`を入力して編集を終了できます。<br>
編集が完了したら下記コマンドを実行し、sshdを再起動<br>
`systemctl restart sshd`

正しく変更できている場合、ルートユーザーでログインできなくなっています。<br>
もし、ログインできてしまった場合は設定ファイルの編集ミスか設定ファイルの再読み込みができていない可能性があるので確認して下さい。<br>

以上で「Rocky Linuxでsshを使用する手順」終了です、お疲れさまでした。
