# 1.ベースイメージの指定
FROM ubuntu:20.04

# 2.PHPのインストール(1つのレイヤーとしてまとめるた為に&&を使用)
# 以下のコマンドは、UbuntuのリポジトリにあるPHPのバージョンが古いため、
# Ondrej PPAを追加してPHP8.0をインストールしている
RUN apt update                                       && \
    apt install -y software-properties-common        && \
    LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php && \
    apt update                                       && \
    apt install -y php8.0 php8.0-mysql

# 3.PHPの設定ファイルをローカルからコンテナ内部へコピー
COPY ./docker/app/mail.ini /etc/php/8.0/cli/conf.d/mail.ini

# 4.msmtp(メールサーバのSMTPクライアント)のインストール
RUN apt install -yqq msmtp msmtp-mta

# 5.msmtpの設定ファイルをローカルからコンテナ内部へコピー
COPY ./docker/app/mailrc /etc/msmtprc

# 6.動作確認用コマンド(群)のインストール
# 必ずしもイメージに含める必要はないが、デバッグや動作確認のためにインストールしておく
RUN apt install -y curl iputils-ping procps vim tree
