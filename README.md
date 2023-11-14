#   Курсовая 7. DRF
Контекст

В 2018 году Джеймс Клир написал книгу «Атомные привычки», которая посвящена приобретению новых полезных привычек и 
искоренению старых плохих привычек. Заказчик прочитал книгу, впечатлился и обратился к вам с запросом реализовать 
трекер полезных привычек.

**В рамках учебного курсового проекта реализована бэкенд-часть SPA веб-приложения.**

**Критерии приемки курсовой работы**
1. Настроить CORS.
2. Настроить интеграцию с Telegram.
3. Реализовать пагинацию.
4. Использовать переменные окружения.
5. Все необходимые модели описаны или переопределены.
6. Все необходимые эндпоинты реализованы.
7. Настроить все необходимые валидаторы.
8. Описанные права доступа заложены.
9. Настроить отложенную задачу через Celery.
10. Проект покрыть тестами как минимум на 80%.
11. Код оформить в соответствии с лучшими практиками.
12. Имеется список зависимостей.
13. Результат проверки Flake8 равен 100%, при исключении миграций.
14. Решение выложено на GitHub.


`**Модели**`
В книге хороший пример привычки описывается как конкретное действие, которое можно уложить в одно предложение:

я буду [ДЕЙСТВИЕ] в [ВРЕМЯ] в [МЕСТО]

За каждую полезную привычку необходимо себя вознаграждать или сразу после делать приятную привычку. Но при этом привычка не должна расходовать на выполнение больше 2 минут. Исходя из этого получаем первую модель — Привычка.

## Привычка:

Пользователь — создатель привычки.
Место — место, в котором необходимо выполнять привычку.
Время — время, когда необходимо выполнять привычку.
Действие — действие, которое представляет из себя привычка.
Признак приятной привычки — привычка, которую можно привязать к выполнению полезной привычки.
Связанная привычка — привычка, которая связана с другой привычкой, важно указывать для полезных привычек, но не для приятных.
Периодичность (по умолчанию ежедневная) — периодичность выполнения привычки для напоминания в днях.
Вознаграждение — чем пользователь должен себя вознаградить после выполнения.
Время на выполнение — время, которое предположительно потратит пользователь на выполнение привычки.
Признак публичности — привычки можно публиковать в общий доступ, чтобы другие пользователи могли брать в пример чужие привычки.
Обратите внимание, что в проекте у вас может быть больше, чем одна описанная здесь модель.

## Валидаторы

Исключить одновременный выбор связанной привычки и указания вознаграждения.
Время выполнения должно быть не больше 120 секунд.
В связанные привычки могут попадать только привычки с признаком приятной привычки.
У приятной привычки не может быть вознаграждения или связанной привычки.
Нельзя выполнять привычку реже, чем 1 раз в 7 дней.
Пагинация
Для вывода списка привычек реализовать пагинацию с выводом по 5 привычек на страницу.
Права доступа
Каждый пользователь имеет доступ только к своим привычкам по механизму CRUD.
Пользователь может видеть список публичных привычек без возможности их как-то редактировать или удалять.
Эндпоинты
Регистрация
Авторизация
Список привычек текущего пользователя с пагинацией
Список публичных привычек
Создание привычки
Редактирование привычки
Удаление привычки
Интеграция
Для полноценной работы сервиса необходим реализовать работу с отложенными задачами для напоминания о том, в какое время какие привычки необходимо выполнять.

Для этого потребуется интегрировать сервис с мессенджером Telegram, который будет заниматься рассылкой уведомлений.

Инструкция по интеграции с Telegram
Для создания Telegram-бота найдите в чате самого главного бота: https://t.me/BotFather.

Начните с ним диалог и выберите команду создания нового бота:
img.png

BotFather предложит ввести имя вашего бота:
img.png

Здесь нужно указать видимое имя бота, т. е. то, которое отображается пользователям. Например, HabbitBot.

После этого BotFather спросит юзернейм вашего бота.
img.png
Здесь бота нужно назвать уникально — это тот уникальный идентификатор, по которому бота можно будет найти. Также важно, чтобы имя заканчивалось на _bot.

Например, habbit_bot.

Если имя подходит под все правила, BotFather предоставит токен и полезные ссылки для использования бота:
img.png
Токен будет использован ботом для обращения к API Telegram-сервисов, поэтому его необходимо сразу сохранить и не распространять.

Безопасность
Для проекта необходимо настроить CORS, чтобы фронтенд мог подключаться к проекту на развернутом сервере.

Документация
Для реализации экранов силами фронтенд-разработчиков необходимо настроить вывод документации. При необходимости эндпоинты, на которые документация не будет сгенерирована автоматически, описать вручную.


masha_habits_bot