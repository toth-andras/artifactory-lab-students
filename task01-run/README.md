# Задание 1. Запуск стенда

**Что делаем:** поднимаем Artifactory из готового compose-файла.

**Зачем:** всё занятие проходит на этом стенде. Пока он не запущен,
дальше двигаться нельзя.

## Шаг 1. Проверьте, что Docker работает

Откройте терминал и выполните:

```bash
docker version
```

- Если видите версии клиента и сервера — всё хорошо.
- Если ошибка — запустите Docker Desktop (или `colima start`) и повторите.

## Шаг 2. Перейдите в корень репозитория

```bash
cd artifactory-lab-students
```

Убедитесь, что вы на месте — рядом должен лежать `docker-compose.yml`:

```bash
ls docker-compose.yml
```

## Шаг 3. Запустите стенд

```bash
docker compose up -d
```

Команда поднимет два контейнера: `artifactory` и `artifactory-postgres`
(Artifactory хранит свои данные в базе PostgreSQL — откройте
`docker-compose.yml` и найдите, как приложение узнаёт про базу:
переменные `JF_SHARED_DATABASE_*`).

## Шаг 4. Проверьте, что контейнеры запущены

```bash
docker compose ps
```

## Результат

В выводе две строки: `artifactory` и `artifactory-postgres`, статус `Up`.

**В отчёт:** вывод `docker compose ps`.
<img width="1714" height="222" alt="image" src="https://github.com/user-attachments/assets/f042a707-635f-4536-89fb-9a4b6f3ab588" />



## Если не получилось

- `ports are not available` — порты 8081/8082 заняты. Скажите преподавателю
  или поменяйте левую часть портов в `docker-compose.yml` на `18081`/`18082`.
- Образ скачивается долго — это нормально, он ~1.5 ГБ.
