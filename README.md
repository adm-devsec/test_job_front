# Тестовое задание
Необходимо разработать тестовое одностраничное web-приложение. Весь ваш код поместитить в один файл index.html. Файл должен нормально открываться на ОС Windows. Все внешние зависимости (JQuery, Bootstrap и прочее) подключать из облачных CDN.

Допускается использовать стандартные возможности JavaScript + JQuery, Bootstrap 5, Chart.js.
Для обращаения к API использовать функцию fetch.

**Описание API - в конце задания.**

**Примерные скриншоты результата лежат в этом репозитории.**

Итоговый файл index.html выложить в личный репозиторий на GitHub и прислать ссылку на него.

# Задачи 

1. На странице должна быть отображена таблица (использовать таблицы Bootstrap). После загрузки страницы, обратиться к API для получения списка приложений и заполнить ими таблицу. API возвращает несколько массивов со свойствами приложений. Чтобы получить данные приложения № 1 - необходимо взять данные по индексу "0" из каждого массива. Для приложения №2 - индекс "1" и так далее.

2. В каждой строке строке таблицы сделать кнопку для изменения приложения. При нажатии на эту кнопку показать модальное окно (Bootstrap) и заполнить его данными конкретного приложения. Все данные в модальном окне, кроме app_id - доступны для редактирования, app_id - доступно только чтение. Внизу модального окна 2 кнопки - "Закрыть" и "Сохранить". При нажатии на кнопку "Сохранить" - вызывается API для изменения приложения. В ответ приходит объект {"error":"0"} или {"error":"1"}. Если error=0 - закрываем модальное окно и обновляем список приложений в таблице (должны измениться данные приложения в таблице). Если error=1 вывести сообщение об ошибке. Ошибка возникает, если не найдено приложение с указанным app_id.

3. Над таблицей сделать кнопку "Добавить приложение". При нажатии на кнопку показать модальное окно (аналогичное по полям п. 2). Все поля пустные и доступны для редактирования. Внизу модального окна 2 кнопки - "Закрыть" и "Сохранить". При нажатии на кнопку "Сохранить" - вызывается API для создания приложения. В ответ приходит объект {"error":"0"} или {"error":"1"}. Если error=0 - закрываем модальное окно и обновляем список приложений в таблице (должно появиться новое приложение). Если error=1 вывести сообщение об ошибке. Ошибка возникает, приложение с указанным app_id уже существует. app_id не должен повторяться - протестировать это. Ошибка должна выводить прямо в модальном окне текстом.

4. Подключить библиотеку Chart.js. Разместить внизу страницы столбиковую диаграмму. Повторить то, что на скриншоте 3 (примерно). По оси X - шкала времени по минутам.


# Скриншоты

# Описание API

**Запрос для получения всех приложений**
```
POST /Face/App_List HTTP/1.1
Host: checkstatus.website:8099
Content-Type: application/json; charset=utf-8
Content-Length: 2

''
```
**Запрос для создания приложения**
```
POST /Face/New_app HTTP/1.1
Host: checkstatus.website:8099
Content-Type: application/json; charset=utf-8
Content-Length: 124

'{"app_id": "abc", "app_name": "test_app", "policy_id": 10, "agent_js_config": "123123", "correlations_config": "321321"}'
```

**Запрос для изменения приложения (приложение определяется по строковому app_id)**
```
POST /Face/Update_app HTTP/1.1
Host: checkstatus.website:8099
Content-Type: application/json; charset=utf-8
Content-Length: 124

'{"app_id": "abc", "app_name": "test_app", "policy_id": 11, "agent_js_config": "123123", "correlations_config": "321321"}'
```
