Домашнее задание к занятию 4 «Оркестрация группой Docker контейнеров на примере Docker Compose»

Задача 1
Зарегистрируйтесь и создайте публичный репозиторий с именем "custom-nginx" на https://hub.docker.com (ТОЛЬКО ЕСЛИ У ВАС ЕСТЬ ДОСТУП);
![image](https://github.com/user-attachments/assets/e4e3928d-23fc-4494-9f2a-4bc0db5e9eea)
 
скачайте образ nginx:1.21.1;
![image](https://github.com/user-attachments/assets/066f767e-9f88-4949-8b57-567cc0f23220)

 
Создайте Dockerfile и реализуйте в нем замену дефолтной индекс-страницы(/usr/share/nginx/html/index.html), на файл index.html с содержимым:
![image](https://github.com/user-attachments/assets/7dc9a570-d0de-478a-969f-800b10b7b41d)
![image](https://github.com/user-attachments/assets/0fa3bb5e-b0fa-4909-84ac-ae02efb53faf)


Соберите и отправьте созданный образ в свой dockerhub-репозитории c tag 1.0.0 (ТОЛЬКО ЕСЛИ ЕСТЬ ДОСТУП).
![image](https://github.com/user-attachments/assets/d36a1167-10b8-47cb-8a92-faf6fc3201fa)
![image](https://github.com/user-attachments/assets/784025bf-f282-4648-b0b4-a2089d69b646)
![image](https://github.com/user-attachments/assets/56055556-30d0-4be1-87da-5541beca5313)

Ссылка - https://hub.docker.com/repository/docker/mrflid/custom-nginx/general


Задание 2
Запустите ваш образ custom-nginx:1.0.0 командой docker run в соответвии с требованиями:
- имя контейнера "ФИО-custom-nginx-t2"
- контейнер работает в фоне
- контейнер опубликован на порту хост системы 127.0.0.1:8080
![image](https://github.com/user-attachments/assets/ff3cc496-3432-4b81-9ab0-be75b19d408f)

Не удаляя, переименуйте контейнер в "custom-nginx-t2"
Выполните команду date +"%d-%m-%Y %T.%N %Z" ; sleep 0.150 ; docker ps ; ss -tlpn | grep 127.0.0.1:8080 ; docker logs custom-nginx-t2 -n1 ; docker exec -it custom-nginx-t2 base64 /usr/share/nginx/html/index.html
Убедитесь с помощью curl или веб браузера, что индекс-страница доступна.
![image](https://github.com/user-attachments/assets/b4313c63-f4e8-41d0-9817-2f0483fac573)

Убедитесь с помощью curl или веб браузера, что индекс-страница доступна.
![image](https://github.com/user-attachments/assets/e316838b-8889-45c9-8142-9287e64cfafc)


Задание 3
Воспользуйтесь docker help или google, чтобы узнать как подключиться к стандартному потоку ввода/вывода/ошибок контейнера "custom-nginx-t2".
Подключитесь к контейнеру и нажмите комбинацию Ctrl-C.
Выполните docker ps -a и объясните своими словами почему контейнер остановился. 

Ответ: ctrl+c это сочетание клавишдля завершения процесса

Перезапустите контейнер
Зайдите в интерактивный терминал контейнера "custom-nginx-t2" с оболочкой bash.
Установите любимый текстовый редактор(vim, nano итд) с помощью apt-get. - ,Было предустановлен редактор nano
![image](https://github.com/user-attachments/assets/4d0189ab-84dd-4939-9c11-7c23edb450c6)
 

Отредактируйте файл "/etc/nginx/conf.d/default.conf", заменив порт "listen 80" на "listen 81".
Запомните(!) и выполните команду nginx -s reload, а затем внутри контейнера curl http://127.0.0.1:80 ; curl http://127.0.0.1:81.
Выйдите из контейнера, набрав в консоли exit или Ctrl-D.
Проверьте вывод команд: ss -tlpn | grep 127.0.0.1:8080 , docker port custom-nginx-t2, curl http://127.0.0.1:8080. Кратко объясните суть возникшей проблемы.
![image](https://github.com/user-attachments/assets/83654032-7da1-44c8-9b7c-a1988c115882)
![image](https://github.com/user-attachments/assets/4d18ce67-24b0-4786-809e-d879479792ab)
![image](https://github.com/user-attachments/assets/ee0cf623-5f4b-4371-9d56-4bf9307d65ac)
 
Задача №4
Запустите первый контейнер из образа centos c любым тегом в фоновом режиме, подключив папку текущий рабочий каталог $(pwd) на хостовой машине в /data контейнера, используя ключ -v.
Запустите второй контейнер из образа debian в фоновом режиме, подключив текущий рабочий каталог $(pwd) в /data контейнера.
![image](https://github.com/user-attachments/assets/0ef69898-b389-47c6-88a4-e69b5fe52b8d)
 
Подключитесь к первому контейнеру с помощью docker exec и создайте текстовый файл любого содержания в /data.
Добавьте ещё один файл в текущий каталог $(pwd) на хостовой машине.
Подключитесь во второй контейнер и отобразите листинг и содержание файлов в /data контейнера.
![image](https://github.com/user-attachments/assets/91563238-7396-4b08-ac88-c12ebc8ba6e7)
 
Задача 5
Создайте отдельную директорию(например /tmp/netology/docker/task5) и 2 файла внутри него. "compose.yaml" с содержимым:
version: "3"
services:
portainer:
image: portainer/portainer-ce:latest
network_mode: host
ports:
- "9000:9000"
volumes:
/var/run/docker.sock:/var/run/docker.sock
"docker-compose.yaml" с содержимым:
version: "3"
services:
registry:
image: registry:2
network_mode: host
ports:
- "5000:5000"
И выполните команду "docker compose up -d". Какой из файлов был запущен и почему? (подсказка: https://docs.docker.com/compose/compose-application-model/#the-compose-file )
Отредактируйте файл compose.yaml так, чтобы были запущенны оба файла. (подсказка: https://docs.docker.com/compose/compose-file/14-include/)
Выполните в консоли вашей хостовой ОС необходимые команды чтобы залить образ custom-nginx как custom-nginx:latest в запущенное вами, локальное registry. Дополнительная документация: https://distribution.github.io/distribution/about/deploying/
Откройте страницу "https://127.0.0.1:9000" и произведите начальную настройку portainer.(логин и пароль адмнистратора)
Откройте страницу "http://127.0.0.1:9000/#!/home", выберите ваше local окружение. Перейдите на вкладку "stacks" и в "web editor" задеплойте следующий компоуз:
- "9090:80"
Перейдите на страницу "http://127.0.0.1:9000/#!/2/docker/containers", выберите контейнер с nginx и нажмите на кнопку "inspect". В представлении <> Tree разверните поле "Config" и сделайте скриншот от поля "AppArmorProfile" до "Driver".
Удалите любой из манифестов компоуза(например compose.yaml). Выполните команду "docker compose up -d". Прочитайте warning, объясните суть предупреждения и выполните предложенное действие. Погасите compose-проект ОДНОЙ(обязательно!!) командой.

 ![image](https://github.com/user-attachments/assets/6f522881-f2ea-49f5-a907-d16e30597e69)
![image](https://github.com/user-attachments/assets/3331e276-cac8-4389-afb6-4dfb6149e477)
![image](https://github.com/user-attachments/assets/1cd92385-5400-4985-b1f6-60ee455d6b98)
![image](https://github.com/user-attachments/assets/e1c3dbfd-5676-4a8d-8171-75e2f39e1529)
![image](https://github.com/user-attachments/assets/6e0b228f-a12a-49e9-bb7c-2da9332c8b65)
![image](https://github.com/user-attachments/assets/5173ee87-8dcc-4d04-9f48-caf948c20732)
![image](https://github.com/user-attachments/assets/443fb164-5b70-46b7-89c4-69c45dfbff14)


 

 

 

 

 

 
