FROM php:7.4-fpm

# 必要なパッケージをOSにインストール
RUN apt-get update && apt-get install -y \
  curl \
  unzip \
  git \
  zip \
  libonig-dev \
  && docker-php-ext-install pdo pdo_mysql mbstring

# 新しいユーザーを追加
RUN useradd -m laraveluser

# 作業ディレクトリを設定
# このディレクトリは、後続のCOPYやRUNコマンドの基準となる
WORKDIR /var/www

# Composerをインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# アプリケーションのソースコードをコピー
COPY . .
# ファイルを新しいユーザーの所有に変更
RUN chown -R laraveluser:laraveluser /var/www

# 新しいユーザーに切り替え
USER laraveluser

# 依存関係のインストール
RUN composer install

# ポート9000を公開
EXPOSE 9000

# php-fpmを起動するコマンド
CMD ["php-fpm"]
