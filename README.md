# wt-docker-mac
WebTutor-docker-mac

# Перед настройкой
1. Скачайте образ с сайта вебсофта
2. Установиет образ командой `docker load -i *.tar`
3. Склонируйте себе текущий репозиторий

# Настройка
1. В xHttp.ini ставим флаг `X-SHELL-START: 1`
2. Запускаем команду `docker compose up -d mssql`
3. После старта нужно подцепиться к sql
  - Server: 127.0.0.1
  - Username - Берём из .env
  - Password - Берём из .env
4. Выполняем запрос из файла `create_db.sql`
5. Запускаем команду `docker compose up -d wt`
6. Далее выполняем `docker exec wt bash -it`
7. Внутри контейнера выполянем `db set type mssql`
  - Server - mssql
  - Database - WTDB
  - Username - sa
  - Password - из .env
  - Y
  - quit
8. Перезагружаем контейнер `docker restart wt`
9. Снова выполняем `docker exec wt bash -it`
10. Ждём пока каталоги развернутся в БД
11. Запускаем команду `package process std`
12. Выключаем контейнер `docker stop wt`
13. В xHttp.ini вернём флаг `X-SHELL-START: 0`
14. Толкаем контейнер `docker start wt`
15. После старта ломимся на веб админку и там устанавливаем узлу нужный порт.
16. Done
