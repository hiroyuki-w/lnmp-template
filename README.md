## nginx/mysql/phpの開発環境のdocker-composeテンプレート

以下の構成の開発環境を構築します。  
細かい構成は不要で、とりあえず手早く開発環境を作りたい特に利用します。

- nginx 1.18
  - https化済み
- php7.4
- mysql8.0

## 構築方法
```
mkdir develop
cd develop
git clone https://github.com/hiroyuki-w/lnmp-template.git ./

vi .env
# 自由に書き換えます。
# ./backend/ディレクトリに動作させたいPHPプログラム格納
# webサーバのホストを書き換えた場合、ローカルのhostsファイル書き換え

docker-compose build
docker-compose up -d
```

## 確認
- 自己証明書の設定  
./docker/https-portal/[ホスト名]/signed.crt  
ファイルに自動生成した証明書ファイルがあります。  
こちらを開き、「常に信頼する」に変更する。

- アクセス確認  
http://localhost:8021/php.php  
https://localhost:4430/php.php 


