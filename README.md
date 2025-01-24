# Настройка административной панели Hestia на Ubuntu 22.04

Please use a valid emailadress (ex. info@domain.tld).
Please enter admin email address: nagaevrustam@yandex.ru
Please enter FQDN hostname [nagaevrustam.fvds.ru]: hestia.ra.test.ru

После выполнения установки Hestia на наш сервер, отправляются логин и пароль учетной записи на почту, которую ввели ранее. У меня пришло письмо и попало в Спам.

* Поменял Port:
Port: 2473

* Перезапустил службу.
При переходе на наш сервер в панель администрирования появилась ошибка (возможно по причине только купленного виртуально сервера и ни разу еще не переустановленная ОС):

Unable to load required libraries. Please run v-add-sys-dependencies in command line. Error: Failed opening required 'vendor/autoload.php' (include_path='.:')

Переводиться: Невозможно загрузить требуемые библиотеки. Запустите v-add-sys-dependencies в командной строке. Ошибка: Не удалось открыть требуемый 'vendor/autoload.php' (include_path='.:')

Необходимо выполнить следующее:
Для запуска команды v-add-sys-dependencies в Hestia Control Panel нужно выполнить команду по адресу: 
/usr/local/hestia/bin/v-add-sys-dependencies

По информации с форума HestiaCP, если при запуске команды возникает ошибка, можно попробовать отладить её с помощью команды: 
bash -x /usr/local/hestia/bin/v-add-sys-dependencies 2>&1 | tee /tmp/v-add-sys-dependencies.log
(Проверил. Работает)

Также, если вывод команды большой и установлен netcat, можно выполнить команду: 
cat /tmp/v-add-sys-dependencies.log | nc termbin.com 9999
 и посмотреть полученный URL.


* Создание учетной записи admin для панели Hestia (первый раз была проблема не мог войти, используя пароль. Помогла переустановка ОС):
Учетная запись администратора панели Hestia:
Логин: admin
Пароль: adminRustam5!

* При входе в административную панель создаем дополнительных пользователей
Учетная запись обычного пользователя панели Hestia:
Логин: ranagaev
Пароль: userRustam5!
