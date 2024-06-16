FROM node:18

# 作業ディレクトリを設定する
WORKDIR /app

# パッケージファイルをコピーして依存関係をインストールする
COPY package.json package-lock.json ./
RUN npm install

# アプリケーションのソースコードをコピーする
COPY . .

# アプリケーションを実行するためのポートを公開する
EXPOSE 3000

# 開発環境用のコマンドを指定する
CMD ["npm", "run", "dev"]
