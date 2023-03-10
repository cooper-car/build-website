## 使用 AWS lightsail 建置個人網站
由於已經在本機透過docker寫好網站，只需要將code和db table放到網站上去\
基本上透過官方文件就可以將網站設定完成

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

### Point domain to lightsail
- Networking 
  - Create and assign a Static IP address to an instance

- Domain & DNS
  - create a DNS zone
  - 把 Name servers 資訊貼到購買網址的後台
  - create DNS records & SSL憑證
    - 參考這部影片： https://www.youtube.com/watch?v=LDVQhN7zJvQ
  
### trouble shooting
- Laravel遇到權限上的問題\
https://stackoverflow.com/questions/72877284/laravel-docker-permission-denied-the-exception-occurred-while-attempting-to-log

### reference
https://docs.bitnami.com/aws/infrastructure/lamp/get-started/use-laravel \
https://docs.bitnami.com/general/how-to/understand-bncert/#certificates-not-renewed-automatically

