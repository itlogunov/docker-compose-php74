### поднять контейнер
`docker-compose up -d`

### опустить контейнер
`docker-compose down`

---

### сайт доступен по ссылке 
#### `http://localhost`

### для битрикса
заменить содержимое конфига nginx на `_docker/config/nginx/nginx_bitrix.conf`

---

### войти в bash
`docker exec -it project_app bash`

### перезагрузить nginx, не входя в bash
`docker exec project_nginx nginx -s reload`

---

### в .env указывать
`DB_CONNECTION=mysql`
`DB_HOST=db` - имя контейнера с бд
`DB_PORT=3306`
`DB_DATABASE=db`
`DB_USERNAME=root`
`DB_PASSWORD=root`

---

### в sequel указывать
`type: tcp/ip`
`host: localhost`
`user: root`
`password: root`
`port: 8886`

---

### smtp
#### в .env указать:
`MAIL_HOST=smtp.yandex.ru
MAIL_PORT=587
MAIL_USERNAME=почта@yandex.ru
MAIL_PASSWORD=пароль_приложения
MAIL_ENCRYPTION=tls`

---

### xdebug
#### в настройках phpstorm создать новый сервер:
`name=Docker
host=Docker
port=80(внутренний порт nginx)
/ указать директорию проекта и путь на сервере /var/www, а затем добавить php-интерпретатор`