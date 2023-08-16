ДИПЛОМНЫЙ ПРОЕКТ ПО АВТОМАТИЗАЦИИ ТЕСТИРОВАНИЯ SKILLFACTORY QAP-120 

Задача: протестировать новый интерфейс авторизации в личном кабинете от заказчика Ростелеком.

Объект тестирования: https://b2c.passport.rt.ru


[Требования по проекту (.doc)](https://docs.google.com/document/d/17TDVf3PazYzNWZ4w95O1HhfkZvXOskdqegHEWtyAwaA/edit?usp=sharing)


Заказчик передал следующее задание:

1. Протестировать требования.
2. Разработать тест-кейсы (не менее 15). Необходимо применить несколько техник тест-дизайна.
3. Провести автоматизированное тестирование продукта (не менее 20 автотестов). Заказчик ожидает по одному автотесту на каждый написанный тест-кейс. Оформить свой набор автотестов в GitHub.
4. Оформить описание обнаруженных дефектов. Во время обучения вы работали с разными сервисами и шаблонами, использовать их для оформления тест-кейсов и обнаруженных дефектов. (если дефекты не будут обнаружены, то составить описание трех дефектов)

Ожидаемый результат

1. Перечислены инструменты, которые применялись для тестирования.

   * Почему именно этот инструмент и эту технику.
   * Что им проверялось.
   * Что именно в нем сделано.
   
2. К выполненному заданию прикреплены:

   * Набор тест-кейсов;
   * Набор автотестов на GitHub. Обратите внимание, что в репозитории должен находиться файл README.md, где будет описано, что именно проверяют данные тестовые сценарии и какие команды необходимо выполнить для запуска тестов. Описанные команды должны работать на любом компьютере с установленными Python3 и PyTest;
   * Описание оформленных дефектов.


В корневом каталоге проекта содержатся:
* [conftest.py](https://github.com/CricetusS/QAP120_Final/blob/master/conftest.py) - содержит условия для выполнения тестов.
* [pytest.ini](https://github.com/CricetusS/QAP120_Final/blob/master/pytest.ini) - содержит указание на автоматическую генерацию html-отчета.
* [README.md](https://github.com/CricetusS/QAP120_Final/blob/master/README.md) - содержит информацию в целом о проекте.
* [requirements.txt](https://github.com/CricetusS/QAP120_Final/blob/master/requirements.txt) - содержит все библиотеки и зависимости проекта.
***
Директория pages содержит:
* [base_page.py](https://github.com/CricetusS/QAP120_Final/blob/master/pages/base_page.py) - общие методы и утилиты для всех страниц.
* [auth_page.py](https://github.com/CricetusS/QAP120_Final/blob/master/pages/auth_page.py) - специфичные методы и утилиты для страницы авторизации.
***
Директория tests содержит:
* [assets](https://github.com/CricetusS/QAP120_Final/tree/master/tests/assets) - CSS-стили для html-отчёта.
* [base_test.py](https://github.com/CricetusS/QAP120_Final/blob/master/tests/base_test.py) - базовый тестовый класс.
* [test_auth.py](https://github.com/CricetusS/QAP120_Final/blob/master/tests/test_auth.py) - автотесты для страницы авторизации.
***
Директория utilities содержит:
* [locators.py](https://github.com/CricetusS/QAP120_Final/blob/master/utilities/locators.py) - локаторы страницы.
* [test_data.py](https://github.com/CricetusS/QAP120_Final/blob/master/utilities/test_data.py) - данные для проверок авторизации.
***


→ [Тест-кейсы (.excel)](https://docs.google.com/spreadsheets/d/1eo70mMYdxrJNwwHgzmv4t3BBtbiUoNU0lFfwW7fr96M/edit?usp=sharing)

→ [Баг-репорты (.excel)](https://docs.google.com/spreadsheets/d/1JxJElhivv0y_1MMpKAQpnNGKRoDpoIKVPEp11TCtdL0/edit?usp=sharing)

При разработке тест-кейсов применены следующие техники тест-дизайна: 
 
* эквивалентное разбиение
* анализ граничных значений
* предугадывание ошибок
* [диаграмма перехода состояния (.png)](https://drive.google.com/file/d/1tixqW6IG3XbxRwjjLQnxd7BoWmYOCsWI/view?usp=sharing)


Инструменты, которые применялись для тестирования.

* Для тестирования сайта был использован 
интсрумент [Selenium](https://www.selenium.dev/).
* Специальный тестовый фреймворк [Pytest](https://docs.pytest.org/).
* Плагин для pytest, который генерирует HTML-отчет по результатам тестов [pytest-html](https://pytest-html.readthedocs.io/en/latest/).
* Опционально можно установить плагин [allure-pytest](https://pypi.org/project/allure-pytest/) и скачать для неё [командную строку](https://repo.maven.apache.org/maven2/io/qameta/allure/allure-commandline/) для генерации красивых html-отчётов.
* Для определения локаторов использовались 
следующие инструменты: [DevTools](https://developer.chrome.com/docs/devto), [ChroPath](https://chrome.google.com/webstore/detail/chropath/ljngjbnaijcbncmcnjfhigebomdlkcjo).

Запуск тестов:
* установить все библиотеки и зависимости: `pip install -r requirements.txt`.
* убедиться, что присутствуют основные браузеры для тестирования - в файле conftest.py у фикстуры initialize_driver можно изменить браузер.
* запустить тесты: `pytest tests/test_auth.py`.
* запустить один тест: `pytest tests/test_auth.py::TestAuth::название_нужного_теста`.

Дополнительно:
Добавлена фикстура для пропуска тестов если на странице присутствует капча. Рекомендуется запускать не более 2-3 тестов, связанных с авторизацией, чтобы избежать появления капчи.
