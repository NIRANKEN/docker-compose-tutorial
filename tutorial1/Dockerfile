# syntax=docker/dockerfile:1

# 今回ベースとして使うDocker imageを選ぶ
FROM python:3.7-alpine

# 作業用ディレクトリの作成
WORKDIR /code

# 環境変数の定義
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0

# コマンドのインストール
RUN apk add --no-cache gcc musl-dev linux-headers

# ローカルの./requirements.txtをコンテナにコピー
COPY requirements.txt requirements.txt

# requirements.txtをもとにpythonのライブラリとってくる
RUN pip install -r requirements.txt

# 5000番ポート使いますよ宣言
EXPOSE 5000

# カレントディレクトリのもの全部コンテナに移動してる(app.pyを多分使いたい)
COPY . .

# やりたいコマンドの実行
CMD ["flask", "run"]