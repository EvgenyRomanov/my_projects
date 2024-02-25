Ранние проекты:  
- [1. Блог "Readme"](https://github.com/EvgenyRomanov/readme.git)  
- [2. Сайт студии дизайна](https://github.com/EvgenyRomanov/studio_website.git)  
- [3. Сайт моды](https://github.com/EvgenyRomanov/bitrix.git)  

Минипроекты (решения представлены как `pull requests` к заданиям в рамках курса OTUS):
1) Описание инфраструктуры в docker-compose, которая включает в себя:
    - nginx (обрабатывает статику, пробрасывает выполнение скриптов в fpm)
    - php-fpm (соединяется с nginx через unix-сокет)
    - redis (соединяется с php по порту)
    - memcached (соединяется с php по порту)
    - БД
  
   [Решение](https://github.com/otusteamedu/PHP_2023/pull/412)
