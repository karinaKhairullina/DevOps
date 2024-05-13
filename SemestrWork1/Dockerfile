# Используем образ Python
FROM python:3.9

# Рабочая директория в /app
WORKDIR /app

# Копирую файл зависимостей в текущую директорию
COPY requirements.txt /app/

# Устанавливаю зависимости из файла requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Копирую все файлы из текущей директории в /app в контейнере
COPY . /app/
