## Ранние проекты  
- [1. Блог "Readme"](https://github.com/EvgenyRomanov/readme.git)  
- [2. Сайт студии дизайна](https://github.com/EvgenyRomanov/studio_website.git)  
- [3. Сайт моды (bitrix)](https://github.com/EvgenyRomanov/bitrix.git)  

## Минипроекты 
Решения представлены как `pull requests` к заданиям в рамках курса OTUS  
### 1)  Описание инфраструктуры в docker-compose.
    Включает в себя:
    - nginx (обрабатывает статику, пробрасывает выполнение скриптов в fpm)
    - php-fpm (соединяется с nginx через unix-сокет)
    - redis (соединяется с php по порту)
    - memcached (соединяется с php по порту)
    - БД  
   [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/412)  
   ---  

### 2) Консольное приложение (bash-скрипт).
    Принимает два числа и выводит их сумму в стандартный вывод.  
    Например ./sum.sh 1.5 -7.  
    Если предоставлены неверные аргументы (для проверки на число можно использовать регулярное выражение) вывести ошибку в консоль.  
    Также имеется таблица следующего вида:  
    id user city phone
    1 test Moscow 1234123  
    2 test2 Saint-P 1232121  
    3 test3 Tver 4352124  
    4 test4 Milan 7990923  
    5 test5 Moscow 908213  
    Таблица хранится в текстовом файле.
    Вывести на экран 3 наиболее популярных города среди пользователей системы, используя утилиты Linux.  
[**Решение**](https://github.com/otusteamedu/PHP_2023/pull/446)
--- 

### 3) Свой пакет.  
    В pull-request composer.json, в котором приводится пример подключения пакета.  
[**Решение**](https://github.com/otusteamedu/PHP_2023/pull/488)
--- 

### 4) Браузерное приложение и балансировщик.
    Верификация строки со скобками.  
    Используя Docker, описать сборку двух контейнеров – один с nginx, второй – с php-fpm и кодом.  
    Контейнер с nginx пробрасывает 80 порт на хостовую машину и ожидает соединений.
    Клиент соединяется, и шлёт следующий HTTP-запрос:  

    POST / HTTP/1.1  
    string=(()()()()))((((()()()))(()()()(((()))))))  
    
    String - это POST-параметр, который можно проверять на: непустоту, корректность кол-ва открытых и закрытых скобок.
    Все запросы с динамическим содержимым (*.php) nginx, используя директиву fastcgi_pass, проксирует в контейнер с php-fpm и кодом.
    Nginx должен обрабатывать запросы не обращая внимания на директиву Host.  
    После обработки, если строка корректна, то пользователю возвращается ответ 200 OK, с информационным текстом, что всё хорошо.  
    Если строка некорректна, то пользователю возвращается ответ 400 Bad Request, с информационным текстом, что всё плохо.  
    Создать балансируемый кластер. Балансировщик nginx-upstream. Балансируемые бэкенды на nginx 
    (у каждого свой php-fpm, в идеале - можно запрашивать любой доступный fpm).  
    Подключить к обоим контейнерам fpm контейнер с Memcache.
 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/492)
---   

### 5)  Консольный чат на сокетах.  
    Создать логику, размещаемую в двух php-контейнерах (server и client), объединённых общим volume.  
    Скрипты запускаются в режиме прослушивания STDIN и обмениваются друг с другом вводимыми сообщениями через unix-сокеты.  
    
    Cервер поднимается всегда первым. Клиент ожидает ввод из STDIN и отправляет сообщения серверу.  
    Сервер выводит полученное сообщение в STDOUT и отправляет клиенту подтверждение (например, "Received 24 bytes").  
    Клиент выводит полученное подтверждение в STDOUT и начинает новую итерацию цикла.  
 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/520)
---   

### 6)  Приложение верификации email.  
    Реализовать приложение (сервис/функцию) для верификации email.
    Минимальный функционал - список строк, которые необходимо проверить на наличие валидных email.
    Валидация по регулярным выражениям и проверке DNS mx записи, без полноценной отправки письма-подтверждения.  
 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/528)
--- 
    
### 7) Проектирование схемы данных для системы управления кинотеатром.  
    Кинотеатр имеет несколько залов, в каждом зале идет несколько разных сеансов, клиенты могут купить билеты на сеансы.
    Спроектировать базу данных для управления кинотеатром.
    Задокументировать с помощью логической модели.
    Написать DDL скрипты.
    Написать SQL для нахождения самого прибыльного фильма.

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/542)
--- 

### 8) Leetcode.
    https://leetcode.com/problems/merge-two-sorted-lists/  

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/559)
--- 

### 9) Спроектировать EAV-хранение для базы данных кинотеатра.  
    4 таблицы: фильмы, атрибуты, типы атрибутов, значения.
    Типы атрибутов и соответствующие им атрибуты (для примера):
    - рецензии (текстовые значения) - рецензии критиков, отзыв неизвестной киноакадемии ...
    - премия (заменяется при печати баннеров и билетов на изображение, логическое значение) - оскар, ника ...
    - "важные даты" даты (при печати - наименование атрибута и значение даты, тип дата) - мировая премьера, премьера в РФ ...
    - служебные даты (используются при планировании, тип дата) - дата начала продажи билетов, когда запускать рекламу на ТВ ...
    
    View сборки служебных данных в форме:
    фильм, задачи актуальные на сегодня, задачи актуальные через 20 дней.
    
    View сборки данных для маркетинга в форме (три колонки):
    фильм, тип атрибута, атрибут, значение (значение выводим как текст).

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/590)
--- 

### 10) Индексирование данных.  
    Подготовить список из 6 основных запросов к БД:
    - выбор всех фильмов на сегодня
    - подсчёт проданных билетов за неделю
    - формирование афиши (фильмы, которые показывают сегодня)
    - поиск 3 самых прибыльных фильмов за неделю
    
    Сформировать схему зала и показать на ней свободные и занятые места на конкретный сеанс.
    Вывести диапазон миниальной и максимальной цены за билет на конкретный сеанс.
    Целесообразно выбрать 3 "простых" (задействована 1 таблица), 3 "сложных" (агрегатные функции, связи таблиц).
    Далее нужно заполнить таблицы, увеличив общее количество строк текстовых данных до 10000.
    Затем провести анализ производительности запросов к БД, сохранить планы выполнения.
    Заполнить таблицы, увеличив общее количество строк текстовых данных до 10000000.
    Затем провести анализ производительности запросов к БД, сохранить планы выполнения.
    На основе анализа запросов и планов предложить оптимизации (индексы, структура, параметры и др.)
    Добавить индексы и сравнить результат, приложив планы выполнения.  

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/623/files#diff-a22350b28862150572f20bd8fc9de640d6fb5d9a0435c61423ad6d6ab8f96369)
--- 

### 11) ElasticSearch.  

    Реализовать поиск по книжному интернет-магазину с помощью Elasticsearch.
    У каждого товара есть название, категория, цена и кол-во остатков на складе.
    Поиск должен корректно работать с опечатками и русской морфологией.
    Пример: пользователь ищет все исторические романы дешевле 2000 рублей (и в наличии) по поисковому запросу "рыцОри".
    В результате должны вернуться товары, ранжированные по релевантности
    Нужно разработать консольное PHP-приложение, которое принимает один или несколько параметров командной строки 
    и выводит результат в виде текстовой таблички, после чего завершает работу.

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/627)
--- 

### 12) Redis.  

    Система должна хранить события, которые в последующем будут отправляться сервису событий.
    События характеризуются важностью (аналитик готов выставлять важность в целых числах).
    События характеризуются критериями возникновения. Событие возникает только если выполнены все критерии его возникновения. 
    Для простоты все критерии заданы так: <критерий>=<значение>.
    Таким образом предположим, что аналитик заносит в систему следующие события:
    {
        priority: 1000,
        conditions: {
        param1 = 1
        },
        event: {
            ::event::
        },
    },
    {
        priority: 2000,
        conditions: {
            param1 = 2,
            param2 = 2
        },
        event: {
            ::event::
        },
    },
    {
        priority: 3000,
        conditions: {
            param1 = 1,
            param2 = 2
        },
        event: {
            ::event::
        },
    }
    
    От пользователя приходит запрос:
    {
        params: {
            param1 = 1,
            param2 = 2
        }
    }
    
    Под этот запрос подходят первая и третья запись, т.к. в них обеих выполнены все условия, но приоритетнее третья, так как имеет больший priority.
    Написать систему, которая будет уметь: добавлять новое событие в систему хранения событий, 
    очищать все доступные события, отвечать на запрос пользователя наиболее подходящим событием.

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/649)
--- 

### 13) Паттерны работы с данными.  

    Необходимо реализовать паттерн Active Record для произвольной таблицы. 

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/660)
--- 

### 14) Leetcode.  
    https://leetcode.com/problems/linked-list-cycle/
    https://leetcode.com/problems/letter-combinations-of-a-phone-number/  

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/676)
--- 

### 15) Паттерны.  
    Задача https://github.com/otusteamedu/PHP_2023/pull/694/files#diff-80de932cadfdfae6ad9731e8f3bd3544fed09b0a70238a514b99d1d5929c6e64

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/694)
--- 

### 16) Разработка кейсов тестирования.  
    Скачать файл с заданием https://drive.google.com/file/d/1yAtmj9DE2yFeGh26WxDwr42j7RVbB_PI/view?usp=sharing
    Внутри файла содержится задача.  

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/730)
--- 

### 17) Leetcode.  
    https://leetcode.com/problems/intersection-of-two-linked-lists/
    https://leetcode.com/problems/fraction-to-recurring-decimal/

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/822)
--- 

### 18) Работа с очередью.  
    Создать простое веб-приложение, принимающее POST запрос из формы от пользователя. 
    Например, запрос на генерацию банковской выписки за указанные даты.
    Обычно такие запросы (в реальных системах) работают довольно долго, поэтому пользователя надо оповестить о том, что запрос принят в обработку.
    Форма должна подразумевать отправку оповещения по результатам работы.
    Передать тело запроса в очередь.
    Написать скрипт, который будет читать сообщения из очереди и выводить информацию о них в консоль.

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/894)
--- 

### 19) API.  

    Необходимо реализовать Rest API с использованием очередей.
    Ваши клиенты будут отправлять запросы на обработку, а вы будете складывать их в очередь и возвращать номер запроса.
    В фоновом режиме вы будете обрабатывать запросы, а ваши клиенты периодически, используя номер запроса, будут проверять статус его обработки.

 [**Решение**](https://github.com/otusteamedu/PHP_2023/pull/904)
--- 
