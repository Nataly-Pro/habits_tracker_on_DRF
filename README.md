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

**Проект может быть размещён на удаленном сервере.** 
Для запуска необходимо выполнить следующие шаги на сервере:
1. установить необходимые программы:

    apt install nginx postgresql postgresql-contrib python3-venv mc
2. установить docker и docker-compose:
    
    apt install docker docker-compose
3. перейти в нужную директорию и скопировать проект из репозитория на сервер:
    
    git clone <GitLab_SSH_code>
4. создать и активировать виртуальное окружение и установить зависимости из проекта:
    
    python3 -m venv env

    source env/bin/activate

    pip3 install -r requirements.txt 
5. создать в проекте файл .env и указать значения переменных:
    
    cp .env_example .env 
6. Создать конфигурацию веб-сервера Nginx для проекта в папке /etc/nginx/sites-available:
    
    mcedit /etc/nginx/sites-available/habits 

следующего вида:
    
    server {
    
        listen 80;
    
        server_name <ip адрес или доменное имя сервера>;
    
        location /static/ {
                        root /path/to/your/project/;
        }
        location /media/ {
                        root /path/to/your/project/;
        }
        location / {
                    include proxy_params;
                    proxy_pass http://127.0.0.1:8000;
        }
    }

7. Проверить корректность настроек Nginx:
    
    nginx -t

8. Подключить сайт к отображению и запустить nginx:
    
    ln -s /etc/nginx/sites-available/habits /etc/nginx/sites-enabled/
    
    systemctl start nginx

9. Запустить приложение с использованием Docker Compose командой: 
    
    docker-compose up --build -d

10. Открыть веб-страничку по IP сервера.


