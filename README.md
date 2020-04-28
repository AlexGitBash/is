# Information Security

## lesson 1
``` bash
sudo apt install git
sudo apt install curl
sudo apt install nginx
sudo nginx
// проверка запуска
ps aux | grep nginx
// редактирование файла
sudo gedit [file_name]
// настройка сервера
cd /etc/nginx/sites-available/
// скопирование файла
sudo cp default test.conf
cd /etc/nginx/sites-enabled/
// создание ссылки
sudo ln -s ../sites-available/test.conf test.conf
cd /var/log/nginx/
// просмотр логов
tail access.log
// установка php
sudo apt install php-fpm
// установка mysql
sudo apt install mysql-server
sudo mysql_secure_installation
// установка burp suite
bash burpsuite.sh
// остановка nginx
sudo nginx -s stop
// перезапуск nginx
sudo nginx -s reload
```

## lesson 2
* //mail.ru
* /blog/post.txt
* ?post=1
* #post1
* http://localhost
* https://geekbrains.ru
* mailto:test@mail.ru
* tel:+79808080808
* file:///var/www/html/index.html
* javascript:alert("XSS")
* data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTJyk8L3NjcmlwdD4=
``` bash
// декодирование base64
echo "PHNjcmlwdD5hbGVydCgnWFNTJyk8L3NjcmlwdD4=" | base64 -d
// получение IP
host geekbrains.ru
// получение информации об IP
whois 5.61.239.22
// изменение hosts
sudo gedit /etc/hosts
```

## lesson 3
``` bash
// подключение к серверу по порту
telnet [host] [port]
// запрос
[method] [path]?[params] [protocol]
Host: [host]
Referer: [url]
// вывод закоровков запросов и ответов
curl -i [host] | less
// вывод запросов больше информации
curl -v [host] 2>&1 | less
```

* 1** - информационная
* 2** - успешный
* 3** - перенаправление
* 4** - ошибка в запросе
* 5** - ошибка на сервере

``` html
// запрет передачи url ref
<meta name="referrer" content="no-referrer">
```

## lesson 4
``` html
<!DOCTYPE html>
<html lang="ru">

<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <link rel="stylesheet" href="/style.css">
  <style>
    html,
    body {
      height: 100%;
      margin: 0;
      padding: 0;
      background-color: #ffffff;
    }
    .wrapper {
      display: flex;
      flex-direction: column;
      height: 100%;
      min-width: 320px;
      min-height: 320px;
      margin: 0 auto;
      font-family: sans-serif;
      color: #000000;
    }
    .wrap-container {
      display: flex;
      flex: 1 0 auto;
      flex-direction: column;
    }
    .footer {
      flex: 0 0 auto;
    }
  </style>
</head>

<body>
  <a href="javascript:alert('XSS')" target="_blank">Sale 80%!</a>
  <form action="/" method="post">
    <input type="text" name="name"><br>
    <input type="text" name="phone"><br>
    <button type="submit">Send form</button>
  </form>
  <iframe src="" frameborder="0" sandbox="allow-same-origin allow-top-navigation allow-scripts"></iframe>
  <script src="/script.js"></script>
  <script>
    window.onload = function() {
      alert('Hello JS!');
    }
  </script>
</body>

</html>
```

## lesson 5
``` javascript
var a = 1;
let b = 'string';
const c = [a, b];

function log(a, b) {
  return a + ' ' + b;
}

if (c) {
  console.log(log(a, b));
}

document.querySelector('h1').innerHTML = 'Caption';

fetch('https://geekbrains.ru/');
```

## lesson 6
* XSS - межсайтовый скриптинг
* SOP - запрещает скрипты между документами
* CSP - защита от XSS, уменьшает вред [Справочник](https://content-security-policy.com/)
* CORS - ослабляет политику SOP [Справочник](https://enable-cors.org/index.html)

## lesson 7
* Origin [scheme + hostname + port]
``` javascript
localStorage.color = 'red';
```

## lesson 8
* PostMessage - передача сообщений между окнами
``` javascript
const target = window.open('http://hostname/page/');
let message = 'string';
target.postMessage(message, 'http://hostname');

// page
window.addEventListener('message', function(event) {
  event.origion === 'http://localhost' && console.log(event.data);
});
```
* WebSocket - постоянное соединение с сервером (wss:)
``` javascript
// Создает WebSocket - подключение.
const socket = new WebSocket('ws://localhost:8080');

// Соединение открыто
socket.addEventListener('open', function (event) {
    socket.send('Hello Server!');
});

// Наблюдает за сообщениями
socket.addEventListener('message', function (event) {
    console.log('Message from server ', event.data);
});
```
