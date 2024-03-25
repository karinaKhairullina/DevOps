# DevOps

## HW1:
Задание:
Написать bash скрипт который создаст для всех пользователей системы отдельную директорию в корневой директории с именем пользователя и установит для нее права 755. При этом владельцем директории должен быть соответствующий пользователь. Путь до корневого каталога создания директорий, должен определяться через ключ "-d"  или если ключ не задан то должен быть "диалог" для определения пути пользователем. Лог должен писаться и в stdout и в файл.

Шаги:
1)Принимает путь к корневой директории через ключ -d или через диалоговое окно, если ключ не указан.
2)Проверяет существование и доступность указанной корневой директории.
3)Создает директории для всех пользователей системы (кроме системных пользователей) в указанной корневой директории.
4)Устанавливает права на созданные директории: владелец - соответствующий пользователь, права - 755.

Как работать:
1)Скачать скрипт script.sh 
2)Команда: chmod +x script.sh
3)Команда: ./script.sh /Users/karina/ (путь к корневой директории)
Либо указать путь через ключ -d, либо в интерактивном режиме

Проверить права доступа:
ls -ld <путь к директории пользователя>

## HW2:
Задание: 
Задание по Ansible:
написать playbook который должен будет:
Создать пользователя на удаленной машине
Сделать авторизацию ssh по ключам для пользователя
Отключить авторизацию по паролю на сервере
Создать директорию в /opt/ с правами для пользователя.

Шаги:
1)Сгенерированы SSH ключи
2)Добавлен публичный ключ на удаленный хост
3)Создайн файл inventory.ini и внутри указан удаленный хост 
4)Создан файл playbookKarina.yml и описаны задачи для настройки удаленной машины
5)С помощью команды "ansible-playbook playbookKarina.yml -i inventory.ini" запущен playbook
и получен ответ 




















