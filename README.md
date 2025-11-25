# Netology_8-03-hw
# Домашнее задания 8-03 - "Система мониторинга Zabbix"
# Задание 1.

## **1. Описание команд установки PostgresSQL.**
## 1.1 Установка из официального дистрибутива.
### $sudo apt install postgresql postgresql-contrib
### *Пакет postgresql содержит основную систему управления базами данных, а postgresql-contrib — дополнительные модули и утилиты.*
## 1.2 Включаю автоматический запуск при загрузке системы.
### $sudo systemctl enable postgresql

## **2. Установка Zabbix Server.**
## 2.1 Выбор ОС и других параметров для устанвоки Zabbix.
![Скриншот выбранной ОС и параметров](https://github.com/Yuriykup/Netology_8-03-hw/blob/main/images/hw8-03-2.png)
## 2.2 Команды установки Zabbix Server.
## 2.2.1 Переходим в режим суперпользователя root.:
### $ sudo -s
## 2.2.2 Скачиваем репозиторий Zabbix Server 7.4.
### $wget https://repo.zabbix.com/zabbix/7.4/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.4+ubuntu24.04_all.deb
## 2.2.3 Распоковываем скачаный репозиторий.
### $dpkg -i zabbix-release_latest_7.4+ubuntu24.04_all.deb
## 2.2.4 Производим обновление.
### $apt update
## 2.2.5 Установливаем Zabbix Server, интерфейс, агента.
### $apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
## 2.2.6 Создаём пользователя и исходную базу данных.
### $sudo -u postgres createuser --pwprompt zabbix
### $sudo -u postgres createdb -O zabbix zabbix
### *На сервере Zabbix импортирую исходную схему и данные. Будет предложено ввести только что созданный пароль.*
### $zcat /usr/share/zabbix/sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
## 2.2.7 Настройка базы данных для Zabbix-сервера.
### *Вношу изменения в файл /etc/zabbix/zabbix_server.conf*
### DBPassword=password
## 2.2.8 Запустк Zabbix.
### *Для применения изменений перезагружаем сервисы Zabbix, Zabbix агента и сервер Apach2.
### $systemctl restart zabbix-server zabbix-agent apache2
### *Активируем запуск при перезагруки ОС*
### $systemctl enable zabbix-server zabbix-agent apache2
## 2.2.9 Запуск интерфейса Zabbix в браузере.
### http://192.168.0.108/zabbix
![Скриншот выбранной ОС и параметров](https://github.com/Yuriykup/Netology_8-03-hw/blob/main/images/hw8-03-1.png)
# **Задание 2-3.**
### *Надеюсь объединение 2го и 3го задания не нарушит требование к выполнению домашнего задания.*
## 1 Скриншот с отображением подлюченных хостов.
![Скриншот с отображением подлюченных хостов](https://github.com/Yuriykup/Netology_8-03-hw/blob/main/images/hw8-03-3.png)
## 2 Лог файл работа Zabbix агента 2 на ОС Windows.
![Лог файл работа Zabbix агента на ОС Windows.](https://github.com/Yuriykup/Netology_8-03-hw/blob/main/images/hw8-03-4.png)
## 3 Лог файл работа Zabbix агента 1 на виртуальной машине где установлена ОС Ubuntu и Zabbix Srever. 
![Лог файл работа Zabbix агента на Zabbix Server.](https://github.com/Yuriykup/Netology_8-03-hw/blob/main/images/hw8-03-5.png)
## 4 Лог файл работа Zabbix агента 2 на второй виртуальной машине где установлена ОС Ubuntu.
![Лог файл работа Zabbix агента на VPC Ubuntu2.](https://github.com/Yuriykup/Netology_8-03-hw/blob/main/images/hw8-03-6.png)
## 5 Сриншот раздела Latest data хоста Client_OS_Windows11 (ОС Windows).
![Сриншот раздела Latest data хоста Client_OS_Windows11](https://github.com/Yuriykup/Netology_8-03-hw/blob/main/images/hw8-03-7.png)
## 6 Описание команд GitHub при выполнении домашнего задания.
### 6.1 Клонирование соданой ветки на портале GitHub.
### git clone https://github.com/Yuriykup/Netology_8-03-hw.git
### 6.2 Добавления файла для загрузки на портал.
### git add images/hw8-03-1.png
### git add README.md
### 6.3 Добавление описаниея внесённых изменений - commit.
### git commit -m "Добавлен файл изображения hw8-03-1.png"
### git commit -m "Файл README.md исправлена ошибка в ссылке на изображение 1"
### 6.4 Загрузка файлов с изменениями на портал GitHub.
### git push origin main 
### 6.5 Проверка статуста загрузки, коммитов, добавлений файлов.
### git status
### 6.6 Скриншот где отображен процесс добавления файлов до внесения комментария и загрузки на GitHub.
![В процессе загрузки на GitHub](https://github.com/Yuriykup/Netology_8-03-hw/blob/main/images/hw8-03-8.png)
 
