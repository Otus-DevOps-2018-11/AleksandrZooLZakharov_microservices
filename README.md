﻿# AleksandrZooLZakharov_microservices

AleksandrZooLZakharov_Microservices repository

Задание Logging-1
Создал отдельный compose-файл logging
Создал образ fluentd
Перенастроил контейнер post на отправку логов через драйвер fluentd.
Настроена Kibana
Донастроен fluentd - описан фильтр для парсинга логов от сервиса post.
Перенастроил контейнер ui на отправку логов через драйвер fluentd
Донастроен fluentd - описаны фильтры с регулярными выражениями (grok) для парсинга логов от сервиса ui.

Задание Monitoring-2
Подготовил окружение, развернул в GCP docker-host (с необходимыми правилами файервола).
Разделил запуск docker-compose на приложения и мониторинг.
Добавил cAdvisor, Grafana (с дашбордами), расширил список мониторируемых приложений.
Нахожу синтаксис PromQL чем-то похожим на SPLUNK (с его SPL)
Установил Alertmanager и настроил получение алертов в свой канал в SLACKе.
Отправил полученные 5 образов (1 новый) на : [DockerHub](https://cloud.docker.com/u/zoolgle/repository/list)

Задание Monitoring-1
Подготовил окружение, развернул в GCP docker-host (с необходимыми правилами файервола).
Запустил Prometheus из Докера. Поизучал его вэб-интерфейс.
Уделил внимание метрикам, их составу и их содержимому. Таргетам.
Донастроил конфиг prometheus и пересоздал образ.
Пересобрал образы ui, post и comment, используя bash docker_build.sh, поправил соответствующий docker-compose.yml, внеся туда и информацию о прометее.
Поправил переменную окружения COMPOSE_TLS_VERSION с TLSv1 на TLSv1_2 - только тогда docker-compose ud -d перестал ругаться на TLS и заработал в облаке GCP.
Убедился что мониторинг отражает действительное состояние сервисов и учитывает зависимости.
Добавил node-exporter, посмотрел как меняется загрузка процессора на хосте.
Отправил полученные 4 образа на : [DockerHub](https://cloud.docker.com/u/zoolgle/repository/list)

Задание Gitlab-CI-1 
Создана виртуальная машина в GCP, установлен Docker, подготовлен docker-compose.yml и окружение. Запущен docker с Gitlab CI. Создал группу, проект, сделал чекаут из своей виртуальной машины с домашками в гитлабовский гит. Сделал пуш, увидел его в гитлабе. Редактировал файл .gitlab-ci.yml, видел как он работает. Создал раннера. Добавил reddit. Добавил окружения. Добавил запуск jobа по кнопке. Ограничил выкатку на stage и prod нетэгированных коммитов. Проверил создание динамически новых окружений при создании новых branchей

Задание Докер-4 
Увидел разницу между сетевыми драйверами none и host. При многократном запуске docker run --network host -d nginx запущеными остаются два инстанса - первый и последний из запускаемых. Запустил проект reddit на bridge-сети. Запустио проект разделенным на front и back end`ы. Посмотрел на docker-proxy. Установил docker-compose. Скачал предложенный файл. Запустил docker-compose, используя переменные окружения. Изменил настроечный файл в логику front-back-end. Параметризовал с помощью .env (включая базовое имя проекта) Базовое имя можно задать несколькими способами (в наименовании не учитываются спецсимволы):

 - изменить имя папки, содержащей docker-compose.yml
 - сделать export COMPOSE_PROJECT_NAME=ваш-вариант
 - COMPOSE_PROJECT_NAME=ваш-вариант можно вложить в .env файл
 - запустить композитора с ключом: docker-compose -p your-project-name up ++ а для контейнеров в .yml файле можно добавить: container_name: your-cont-name

Задание Докер-3 
Взял линтер Hadolint из Docker-образа Ранее созданный инстанс в GCP запущен Развёрнут src, созданы все Dockerfile`s Из трёх образов с первого раза собрался только UI. Ни у кого вопросов не возникало, поэтому возился и решил сам. Пересобрал всё) В post пришлось добавить явную установку gcc и его зависимости. В comment пришлось заменить список репо в etc/apt/sources.list, иначе обновление apt-get (как и apt) заканчивалось ошибкой 404 (адрес репо устарел в этом дистрибутиве) Создана сеть, запущены контейнеры. С линтером слегка уменьшил размер двух образов из трёх - с comment ничего не вышло ^_* Создал и подключил Volume, данные сохраняются после перезапуска контейнеров.

Задание Докер-2 
Создан новый проект в GCP Настроен и инициализирован gcloud, установлен docker-machine и настроен на работу с GCP При повторении практики из демо на лекции видно именно то, о чем говорилось на лекции - в том числе что namespaces ограничивают видимость пидов, что это можно регулировать и т.п. Подготовлены файлы для сборки образа с его установкой, настройкой и стартом нужного сервиса сразу после сборки. Собран образ, запущен контейнер, отправлен в Docker Hub, установлен оттуда и произведены все проверки.

Задание Докер-1 
Настроил проверку Travis-CI (по аналогии с infra) Установлен Докер, запущены Привет мир, собственный контейнер из базового образа убунту. Создан свой образ, изучены базовые команды докер. Описано основное отличие образа от контейнера. (image is read-only stock of layers, but container have read and write fs) Удалены контейнеры и образы.

Рабочее окружение развернуто в чистом образе Ubuntu, всё рабочее окружение настроено заново.