<h1 align="center">Добро пожаловать в b0mb3r 👋</h1>
<p align="center">
    <sub>Открытый и бесплатный СМС бомбер</sub>
    <br /><br />
    <img alt="Made with Python" src="https://img.shields.io/badge/Made%20with-Python-%23FFD242"></img>
    <img alt="Version 2.0" src="https://img.shields.io/badge/version-2.0-blue.svg?cacheSeconds=2592000"></img>
</p>

## 🚀 Установка
1. Установите Python версии не ниже 3.7. Сделать это можно так:
    ### Для Windows или *nix
    Скачайте установщик с [официального сайта](https://www.python.org/downloads/) и запустите его. Убедитесь, что при установке отметили галочку ![Add Python to PATH](https://user-images.githubusercontent.com/42045258/69171091-557d2780-0b0c-11ea-8adf-7f819357f041.png)
    ### Для Android
    Установите приложение [Termux](https://play.google.com/store/apps/details?id=com.termux), запустите его и следуйте [инструкции](https://wiki.termux.com/wiki/Python). Введите следующую команду (при установке нажимайте Enter при каждом запросе):
    ```sh
    pkg install build-essential
    ```

2. Введите следующую команду:
```sh
pip3 install  --upgrade
```

## Запуск
Всё просто! Введите команду <kbd>b0mb3r</kbd> и интерфейс бомбера будет запущен. Команда доступна из любой директории.

## 💻 Расширенное использование
### API
b0mb3r имеет API, которое позволит вам выполнять некоторые действия, доступные через интерфейс, программно. Запросы необходимо отправлять на сервер `127.0.0.1:8080`, перед этим запустив бомбер.

Ответ на каждый запрос к API возвращается в формате JSON и имеет одно обязательное поле: `success`. Оно будет иметь значение _true_, если запрос был обработан или _false_, если возникла ошибка. В случае ошибки в ответ будут добавлены поля `error_code` ([Код ошибки](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP)) и `error_description` (Описание ошибки)
<h1></h1>

### POST `/attack/start`
Начинает атаку на телефон.

| Название параметра | Описание                                                |
|--------------------|---------------------------------------------------------|
| phone_code         | Код страны, например 7                                  |
| phone              | Номер телефона без + и кода страны, например 9123456789 |
| number_of_cycles   | Количество повторений                                   |

**Пример запроса**
```python
import requests

json_ = {
    "phone_code": "7",
    "phone": "9012345678",
    "number_of_cycles": "1"
}

a = requests.post("http://127.0.0.1:8080/attack/start", json=json_)

print(a.json())
```

**Пример ответа**
<img alt="Пример ответа" src="https://user-images.githubusercontent.com/42045258/70137798-da854680-169f-11ea-8133-2f37631292af.png"></img>
