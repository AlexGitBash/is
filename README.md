# Information Security

## lesson 1
``` bush
sudo apt install git
sudo apt install curl
sudo apt install nginx
sudo nginx
// проверка запуска
ps aux | grep nginx
// редактировать файлы
sudo gedit [file_name]
// настройка сервера
cd /etc/nginx/sites-available/
// скопировать файл
sudo cp default test.conf
cd /etc/nginx/sites-enabled/
// создать ссылку
sudo ln -s ../sites-available/test.conf test.conf
cd /var/log/nginx/
// просмотр логов
tail access.log
```
