# Set Up SSH Keys on Rocky Linux
Rocky LinuxでsshKeyを作成する方法について説明します。<br>
※windows/Mac共にbash/zshを使用すれば同じ手順で作成可能です<br>
※windowsの場合はファイルパスが`C:\Users\ユーザー名\.ssh`になります。<br>

## step1
自ユーザーのsshフォルダに移動します。<br>
`cd ~/.ssh/`
上記のコマンドを入力したらsshフォルダに移動できます。

## step2
次にKeyを作成します  
`ssh-keygen -t rsa`
上記のコマンドで作成できます。<br>

ちなみに`ssh-keygen -t rsa`の後ろに`-c 記述したいコメント`を追記する事でコメントを追加できます。

## step3
作成したSSH Keyは<br>
`less ~/.ssh/作成したSSH Keyファイル名`
でSSH Keyの中身を確認できます。<br>

以上で「bash/zshを使ったsshKey作成」終了です、お疲れさまでした。
