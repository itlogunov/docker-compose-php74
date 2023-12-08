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

### xdebug + phpstorm
#### в настройках создать новый `PHP->Servers`:
`Name=Docker`  
`Host=Docker`  
`Port=80(внутренний порт nginx)`  
`Debugger=Xdebug`  
прописать mapping проекта на сервере `/var/www`
#### создать новый `PHP->CLI Interpreter`
указать docker-compose и контейнер, в котором установлен php с xdebug
### настроить `PHP->Debug->DBGp Proxy`
`IDE key: PHPSTORM`  
`Host: host.docker.internal`  
`Port: 9000`
### создать `PHP Remote Debug` конфигурацию в меню `Run/debug configurations` (справа сверху)
`Server: Docker`    
`IDE key (session id): PHPSTORM`
### поставить в браузер расширение `Xdebug helper`
в настройках указать `IDE key: PHPSTORM`
### запуск
поставить брекпоинт  
включить прослушку  
активировать расширение в браузере в режиме debug 
