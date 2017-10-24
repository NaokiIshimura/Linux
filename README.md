# Linux

---

# ユーザ

```
# ユーザ一覧
$ cat /etc/passwd
ユーザー名:パスワード:ユーザID:グループID:コメント:ホームディレクトリ:ログインシェル
```

---

# SELinux

## 基本

```
# 有効化
$ sudo setenforce 1

# 無効化
$ sudo setenforce 0

# 状態確認
$ sudo getenforce
```

```
# 永続化
$ sudo vi /etc/selinux/config

SELINUX=disabled

# 再起動
$ sudo reboot
```

## audit2allow

```
# モジュール内容確認
$ sudo cat /var/log/audit/audit.log | grep nginx | audit2allow -m nginx

# モジュール作成
$ sudo cat /var/log/audit/audit.log | audit2allow -M nginx

# 備考
「nginx」の部分は必要に応じて修正
```

## setmodule

```
# モジュール追加
$ sudo semodule -i nginx.pp

# モジュール削除
$ sudo semodule -r nginx

# モジュール有効化
$ sudo semodule -e nginx

# モジュール無効化
$ sudo semodule -d nginx

# モジュール一覧
$ sudo semodule -l

# 備考
「nginx」の部分は必要に応じて修正
```
