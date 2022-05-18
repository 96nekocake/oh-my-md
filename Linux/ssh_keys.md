# Set Up SSH Keys on Rocky Linux
## step1
自ユーザーのsshフォルダに移動します。<br>
下記コマンドを入力したらsshフォルダに移動できます。<br>
`cd $HOME/.ssh/`

## step2
次にKeyを作成します  
`ssh-keygen -t rsa`
上記のコマンドで作成できます。<br>
 作成する際`ssh-keygen -t rsa`の後ろに`-c 記述したいコメント`を追記する事でコメントを追加できます。

## step3
作成したSSH Keyは<br>
`less ~/.ssh/作成したSSH Keyファイル名`
でSSH Keyの中身を確認できます。<br>

以上でsshKey作成終了です、お疲れさまでした。
