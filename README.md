# 使用 AWS lightsail 建置個人網站

## build a website
由於已經在本機透過docker寫好網站，只需要將code和db table放到網站上去

### tech
- laravel
- mysql
- aws lamp(php7)

### environment
 - apache
   依照官方文件調整 apache configuration
 - phpmyadmin
   - download {name}.pem key (透過console下載)
   - chmod 600 {name}.pem
   - ssh -N -L 8888:127.0.0.1:80 -i {name}.pem bitnami@{server-ip}
   - 貼上 http://127.0.0.1:8888/phpmyadmin 就會看到畫面摟
   - migrate database table
- laravel code
   - 下載相依套件 
     - 進入 lightsail instance的terminal
     - git clone 專案
     - 執行 composer install
     - 執行 composer update (optional)
   - .env檔建立
     - laravel key generate
     - 填上DB password

#### trouble shooting
- 遇到權限上的問題
  https://stackoverflow.com/questions/72877284/laravel-docker-permission-denied-the-exception-occurred-while-attempting-to-log

#### reference
https://docs.bitnami.com/aws/infrastructure/lamp/get-started/use-laravel/

