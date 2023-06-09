Задание 1. Кеширование
Приведите примеры проблем, которые может решить кеширование.

Приведите ответ в свободной форме.

Ответ:

Кеширование — механизм, с помощью которого можно повысить скорость работы приложения за счёт переноса часто используемых данных в очень быстрое хранилище.

Кеширование может решить проблемы:
1. Повышение производительности
2. Увеличение скорости ответа
3. Экономия ресурсов БД (кеширование тяжелых запросов)
4. Сглаживание бустов трафика

Задание 2. Memcached
Установите и запустите memcached.

Приведите скриншот systemctl status memcached, где будет видно, что memcached запущен.

Ответ:

Memchached - это популярный сервер кэширования данных в оперативной памяти. С помощью него можно существенно увеличить производительность различных веб-приложений. Сам по себе Memcached позволяет только сохранять пары ключ-значение в памяти и быстро получать к ним доступ. Обычно Memcached используется вместе с каким-либо языком программирования. Например с Php, Python или серверным JavaScript.

Установка memcached:

apt install memcached

Посмотреть на каком порту висит:
```
netstat -tap | grep memcached
ss –tlpn
```

![screen1](https://github.com/KorolkovDenis/11.2-redis_memcached/blob/main/screenshots/screen1.jpg)

Убедимся, что memcached запущен командой: systemctl status memcached.

![screen2](https://github.com/KorolkovDenis/11.2-redis_memcached/blob/main/screenshots/screen2.jpg)


Задание 3. Удаление по TTL в Memcached
Запишите в memcached несколько ключей с любыми именами и значениями, для которых выставлен TTL 5.

Приведите скриншот, на котором видно, что спустя 5 секунд ключи удалились из базы.

Ответ:

Для подключения к серверу memcached с помощью telnet:

telnet localhost 11211

![screen4](https://github.com/KorolkovDenis/11.2-redis_memcached/blob/main/screenshots/screen4.jpg)

Для того, чтобы сохранить данные, используется команда add. У неё такой синтаксис:

add имя_ключа флаги время_хранения размер_данных
данные

Записываю в memcached несколько ключей, для которых выставлен TTL 5

![screen3](https://github.com/KorolkovDenis/11.2-redis_memcached/blob/main/screenshots/screen3.jpg)

При проверке ключей через 5 секунд они пропадают с кеша.

Но как по мне - такие краткие TTL=5 трудно отслеживать через терминал. Надо успеть команду ввести. get key

Задание 4. Запись данных в Redis
Запишите в Redis несколько ключей с любыми именами и значениями.

Через redis-cli достаньте все записанные ключи и значения из базы, приведите скриншот этой операции.

Ответ:

Сперва установим redis:

apt install redis

Проверим запустился ли он:

systemctl status redis

![screen5](https://github.com/KorolkovDenis/11.2-redis_memcached/blob/main/screenshots/screen5.jpg)

Идем в redis-CLI

![screen6](https://github.com/KorolkovDenis/11.2-redis_memcached/blob/main/screenshots/screen6.jpg)

Ввожу несколько ключей и значений в Redis:

![screen7](https://github.com/KorolkovDenis/11.2-redis_memcached/blob/main/screenshots/screen7.jpg)

Достаю все записанные ключи и значения из базы:

![screen8](https://github.com/KorolkovDenis/11.2-redis_memcached/blob/main/screenshots/screen8.jpg)

Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже разобраться в материале.

Задание 5*. Работа с числами
Запишите в Redis ключ key5 со значением типа "int" равным числу 5. Увеличьте его на 5, чтобы в итоге в значении лежало число 10.

Приведите скриншот, где будут проделаны все операции и будет видно, что значение key5 стало равно 10.



[Моя работа по «Кеширование Redis/memcached»](https://docs.google.com/document/d/1KqfLxv4WqHWxIUg3Z9cTyiKfjaygHxlL/edit?usp=share_link&ouid=104113173630640462528&rtpof=true&sd=true)