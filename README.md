Данный проект - это бэкенд-часть SPA веб-приложения 'Трекер полезных привычек'. 

Пользователь приложения описывает действие, которое хочет превратить в полезную привычку, 
а также время и место выполнения.
Установлены ограничения: 
- периодичность выполнения действия - не реже 1 раза в неделю (по умолчанию ежедневно), 
- время выполнения действия - не более 2-х минут,
- для полезной привычки должно быть указано вознаграждение или связанная приятная привычка.
Приложение шлёт напоминание пользователю в мессенджер Telegram за 10 минут до обозначенного 
времени выполнения действия.
Поэтому при регистрации пользователь указывает свой chat_id.

Для подключения к проекту фронтенд-разработчика настроена автогенерация API-документации.
Ендпоинты протестированы через Postman.

Для быстрого масштабирования проект "завёрнут" в Docker контейнеры (созданы инструкции Dockerfile и docker-compose.yml).
Запуск осуществляется командой: docker-compose up --build 

