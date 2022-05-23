# SELinux簡易まとめ
- SELinux(Security Enhanced Linux)とは
  - システムにアクセス可能なユーザーを制御するシステムセキュリティ
# SELinux のステータス
SELinuxのステータスは`有効`と`無効`の二種存在する。<br>

## SELinux が無効の場合
SELinuxが無効の場合はDAC（Discretionary Access Control）のルールが適用される。

## SELinuxが有効の場合
SELinuxが有効の場合`Enforcing`と`Permissive`の二種類になる。
## Enforcing 
- SELinux のポリシーが強制的に適用される
- インストール後のデフォルトモード
## Permissive
- SELinux のポリシーが強制的に適用されない
- インストール時のデフォルトのモード
:::message
`403 Forbidden`エラーが発生した場合、SELinuxが原因の可能性有
:::

# 参考
- [1.6.2. SELinux の適切な状態の確認](https://access.redhat.com/documentation/ja-jp/red_hat_enterprise_linux/7/html/system_administrators_guide/sec-selinux#doc-wrapper)

## 次に読む
- [SELinux ユーザーおよび管理者のガイド](https://access.redhat.com/documentation/ja-jp/red_hat_enterprise_linux/7/html/selinux_users_and_administrators_guide/index)

