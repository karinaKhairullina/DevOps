
# Здесь использую с веб-сервером Nginx
FROM nginx:latest

# Информация о себе
MAINTAINER Хайруллина_КА

# Устанавливаю PostgreSQL
RUN apt-get update && apt-get install -y postgresql && rm -rf /var/lib/apt/lists/*

# Каталог для хранения данных PostgreSQL
RUN mkdir -p /var/lib/postgresql/data

# Переношу(копирую) файлы Nginx в контейнер
COPY nginx.conf /etc/nginx/nginx.conf
COPY default.conf /etc/nginx/conf.d/default.conf

# Рабочая директория 
WORKDIR /usr/share/nginx/html

# Переменные окружения для настройки PostgreSQL
ENV POSTGRES_USER=user \
    POSTGRES_PASSWORD=password \
    POSTGRES_DB=mydb

# Копирую исходник в контейнер
COPY ./src/ .

# Команда по умолчанию для запуска Nginx
CMD ["nginx", "-g", "daemon off;"]

# Для добавления дополнительных файлов и каталогов в контейнер 
ADD additional_files /usr/share/nginx/html/additional_files 

# Определила точку монтирования 
VOLUME /usr/share/nginx/html/data 

# Здесь задается пользователь, от имени которого будут выполняться команды 

USER nginx

# Открываю порт для доступа к Nginx
EXPOSE 80

