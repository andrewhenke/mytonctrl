## Что это
Данная консольная программа является оберткой над `fift`, `lite-client` и `validator-engine-console`. Она была создана для облегчения управления кошельками, доменами и валидатором на операционной системе `Linux`.
![](https://raw.githubusercontent.com/igroman787/mytonctrl/master/screens/mytonctrl-status_ru.png)

## Функционал
- [x] Показать статус сети TON
- [x] Управление локальными кошельками
	- [x] Создать локальный кошелек
	- [x] Активировать локальный кошелек
	- [x] Показать локальные кошельки
	- [x] Импортировать кошелек из файла (.pk)
	- [x] Сохранить адрес кошелька в файл (.addr)
	- [x] Удалить локальный кошелек
- [x] Показать статус аккаунта
	- [x] Показать баланс аккаунта
	- [x] Показать историю аккаунта
	- [x] Показать статус аккаунта из закладок
- [x] Перевод средств на кошелек
	- [x] Перевод фиксированной суммы
	- [x] Перевод всей суммы (all)
	- [x] Перевод всей суммы с диактивацией кошелька (alld)
	- [x] Перевод средств на кошелек из закладок
	- [x] Перевод средств на кошелек через цепочку самоудаляемых кошельков
- [x] Управление закладками
	- [x] Добавить аккаунт в закладки
	- [x] Показать закладки
	- [x] Удалить закладку
- [x] Управление предложениями
	- [x] Показать предложения
	- [x] Проголосовать за предложение
	- [x] Автоматическое голосование за ранее проголосованные предложения
- [x] Управление доменами
	- [x] Арендовать новый домен
	- [x] Показать арендованные домены
	- [x] Показать статус домена
	- [x] Удалить домен
	- [ ] Автоматическое продление доменов
- [x] Управление валидатором
	- [x] Участвовать в выборах валидатора
	- [x] Возвращать ставку + вознаграждение
	- [x] Автозапуск валидатора при аварийном завершении (systemd)
	- [x] Отправлять статистику валидатора на https://toncenter.com

## Список проверенных операционных систем
```
Ubuntu 16.04 LTS (Xenial Xerus) - Error: TON compilation error
Ubuntu 18.04 LTS (Bionic Beaver) - OK
Ubuntu 20.04 LTS (Focal Fossa) - OK
Debian 8 - Error: Unable to locate package libgsl-dev
Debian 9 - Error: TON compilation error
Debian 10 - OK
```

## Описание установочных скриптов
- `toninstaller.sh` - Данный скрипт клонирует исходники `TON` и `mytonctrl` в папки `/usr/src/ton` и `/usr/src/mytonctrl`, компилирует программы из исходников и прописывает их в `/usr/bin/`.
- `mytoninstaller.py` - Данный скрипт производит настройку валидатора, `mytonctrl` и создание ключей для подключения к валидатору.

## Режимы установки
Есть два режима установки: `lite` и `full`. Оба они **компилируют** и устанавливают компоненты `TON`. Однако `lite` версия не настраивает и не запускает валидатор.

## Установка (Ubuntu)
1. Скачайте и выполните скрипт `install.sh` с нужным вам режимом установки (`<mode>`). В ходе установки у вас будет несколько раз запрошен пароль суперпользователя.
```sh
wget https://raw.githubusercontent.com/igroman787/mytonctrl/master/scripts/install.sh
sudo bash install.sh -m <mode>
```

2. Готово. Можете пробовать запустить программу `mytonctrl`.
```sh
mytonctrl
```

## Установка (Debian)
1. Скачайте и выполните скрипт `install.sh` с нужным вам режимом установки. В ходе установки у вас будет несколько раз запрошен пароль суперпользователя.
```sh
wget https://raw.githubusercontent.com/igroman787/mytonctrl/master/scripts/install.sh
su root -c 'bash install.sh -m <mode>'
```

2. Готово. Можете пробовать запустить программу `mytonctrl`.
```sh
mytonctrl
```

## Телеметрия
По умолчанию `mytonctrl` отправляет статистику валидатора на сервер https://toncenter.com
Это необходимо для выявления аномалий в сети а так же для быстрого реагирования разработчиков.
Для отключения телеметрии при установке воспользуйтесь флагом `-t`:
```sh
sudo bash install.sh -m <mode> -t
```

Для отключения телеметрии после установки:
```sh
MyTonCtrl> set sendTelemetry false
```

## Полезные ссылки
1. https://ton.org/README.txt
2. https://ton.org/HOWTO.txt
3. https://ton.org/FullNode-HOWTO.txt
4. https://ton.org/Validator-HOWTO.txt
5. https://ton.org/TonSites-HOWTO.txt
6. https://ton.org/DNS-HOWTO.txt
7. https://ton.org/ConfigParam-HOWTO.txt