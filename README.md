# hostel
Z-Wave for access to the Philio locks in a mini-hotel
 Описание системы бронирования мини отеля и управления замками комнат, вход в здание и комнаты по кодовым замкам. Система не опробована в реальных условиях.
Операционная среда:
Server Windows 16/Ubuntu 20, Apache 2.4, PHP 7, MySql 5.6, Curl, Forms HTML 5, JS, Z-Wave hub, замок Philio.

Описание работы системы.
Запрос Бронирования через Forms HTML5 (:8081/Hostel/Index.php,/var/www/html/index.phtml, ):
-  в БД создается запись status.client= R(reserve),дата заказа, имя, телефон, e-mail, ip.
В ответ клиенту  e-mail с просбой оплатить до 12:00 дня заезда. 
После оплаты корректируется запись в БД (вводится сумма), пока в ручную.
Ежедневно в пакетном режиме выполняются  scripts(cmd) :
- в 12:00 sched по очистки БД и сбросу ключей замков отбывших посетителей, формируется список комнат для уборки;
- в 14:30 sched_new формирование случайным образом ключей доступа, запись их в замки, пересылка ключей новым сегодняшним посетителям по e-mail, соотвествущие изменения в БД.



Для администратора отеля программы ручного управления замками (открыть, закрыть, удалить, добавить код замка): 
Code_Add_Del.html, ... копируем куда удобно.
При помощи Code_Add_del.html удобно управлять замком Philio в среде Z-Wave, запускается в локальном браузере.
Доступ к тестовой системе бронирования по запросу (необходимио запустить сервер).
