# 1.ベースイメージの取得
# 今回はMySQL5.7のイメージを使用
# 8.0系にはlinux/arm64/v8があるが、5.7系にはそれが無い。
# そのため、アーキテクチャを明示的に指定する必要がある
FROM --platform=linux/amd64 mysql:5.7

# 2.MySQLの設定ファイルをローカルからコンテナ内部へコピー
COPY ./docker/db/my.cnf /etc/my.cnf