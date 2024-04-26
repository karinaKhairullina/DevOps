# DevOps
## HW1:
### Задание:
 Написать bash скрипт который создаст для всех пользователей системы отдельную директорию в корневой директории с именем пользователя и установит для нее права 755. При этом владельцем директории должен быть соответствующий пользователь. Путь до корневого каталога создания директорий, должен определяться через ключ "-d"  или если ключ не задан то должен быть "диалог" для определения пути пользователем. Лог должен писаться и в stdout и в файл.

 ### Шаги:
 #### 1)Принимает путь к корневой директории через ключ -d или через диалоговое окно, если ключ не указан.
 #### 2)Проверяет существование и доступность указанной корневой директории.
 #### 3)Создает директории для всех пользователей системы (кроме системных пользователей) в указанной корневой директории.
 #### 4)Устанавливает права на созданные директории: владелец - соответствующий пользователь, права - 755.

 ### Как работать:
 #### 1)Скачать скрипт script.sh 
 #### 2)Команда: chmod +x script.sh
 #### 3)Команда: ./script.sh /Users/karina/ (путь к корневой директории)
 Либо указать путь через ключ -d, либо в интерактивном режиме

 #### Проверить права доступа:
 ls -ld <путь к директории пользователя>

 ## HW2:
 ### Задание: 
 #### написать playbook который должен будет:
 #### Создать пользователя на удаленной машине
 #### Сделать авторизацию ssh по ключам для пользователя
 #### Отключить авторизацию по паролю на сервере
 #### Создать директорию в /opt/ с правами для пользователя.

 ### Шаги:
 #### 1)Сгенерированы SSH ключи
#### 2)Добавлен публичный ключ на удаленный хост
#### 3)Создайн файл inventory.ini и внутри указан удаленный хост 
#### 4)Создан файл playbookKarina.yml и описаны задачи для настройки удаленной машины
#### 5)С помощью команды "ansible-playbook playbookKarina.yml -i inventory.ini" запущен playbook
и получен ответ 
![Screen](https://github.com/karinaKhairullina/DevOps/blob/main/Снимок%20экрана%202024-03-25%20в%2017.16.02.png)

## HW3:
### Задание:
#### Бонусное задание (совсем необязательное):
#### Та же постановка задачи что и на Ansible, но реализовать надо как роль. Создаваемые пользователи и их открытые ключи для авторизации должны быть определены через vars, и обязательно должно быть тестирование роли через molecule (рекомендую выбрать  Driver/Provider docker)

Дополнительно сделала:
pip install molecule -установка molecule
написание playbook.yml
Создание ключей
Скачала Vagrant 


### Шаги:
#### 1)Создала роль с помощью команды 
ansible-galaxy init role1
#### 2)В файле main.yml определила переменные(role1/vars/main.yml)
#### 3)Далее в tasks/main.yml определила задачи роли(role1/tasks/main.yml)
#### 4)Создала файл конфигурации molecule(role1/molecule/default/molecule.yml)
#### 5)Запустила тесты с помощью команды 
molecule test
#### Для тестирования выбрала драйвер Vagrant
и получила ответ
![Screen](https://github.com/karinaKhairullina/DevOps/blob/main/Снимок%20экрана%202024-04-14%20в%2015.49.59.png)

## HW4:
### Задание:
#### Напишите Dockerfile для создания образа, который будет содержать веб-сервер Apache или Nginx и базу данных MySQL или postgresql. В Dockerfile должны использоваться инструкции: 
#### FROM, MAINTAINER, RUN, CMD, WORKDIR, ENV, ADD, COPY, VOLUME, USER, EXPOSE.
#### Dockerfile должен содержать комментарии с пояснениями того, что делается. 
#### Собранный образ должен иметь имя вида <фамилия>_<инициалы>_image_<текущая дата>. Рядом с dockerfile должен быть скрин, на котором будут видны все слои вашего image и их размер на диске и команда, которой вы это выведете.

### Шаги:
#### 1)Прописала Dockerfile
#### 2)Создала необходимые файлы и папки для работы
#### 3)Собрала образ Docker, использовала команду
` docker build -t khairullina_ka_image_$(date +%Y%m%d) . `

Здесь (date +%Y%m%d) добавляет текущую дату к имени образа

#### 4)Для просмотра слоев образа и их размера на диске использовала команду(Для лучшего поиска сразу ввела имя образа целиком)
` docker history khairullina_ka_image_$(date +%Y%m%d) `

Получила следующее: 
![Screen](https://github.com/karinaKhairullina/DevOps/blob/main/Снимок%20экрана%202024-04-26%20в%2017.59.18.png)


## HW4:
### Задание:
#### Напишите docker compose конфиг, для разворачивания двух контейнеров в одной сети (10.10.10.0/28) типа bridge: 
#### 1 - Nginx или Apache или ваше самописное приложение на выбор, ему должны передаваться конфигурационные файлы через volume, порт 80 из контейнера должен быть доступен на хостовой машине по порту 8080
#### 2 - mysql или postgres, каталог для хранения данных должен монтироваться как docker volume, docker volume должен быть описан в том же конфигурационном файле docker compose. Сервис с БД должен быть доступен из контейнера с веб-сервером по именам new_db, dev_db.

### Шаги:
#### 1)Создала docker-compose файл(docker-compose.yml)
#### 2)Запустила контейнеры с помощью команды
` docker-compose up -d `

Получила следующее:
![Screen](https://github.com/karinaKhairullina/DevOps/blob/main/Снимок%20экрана%202024-04-26%20в%2019.00.20.png)
![Screen](https://github.com/karinaKhairullina/DevOps/blob/main/Снимок%20экрана%202024-04-26%20в%2019.00.34.png)


























