# Отчет по итогам тестирования

## Краткое описание
Проведено автоматизированное тестирование сервиса по покупке туров через интернет-банк.

Общее количество тест-кейсов — **50**.

## При подключении к СУБД MySQL

![image](https://i.gyazo.com/dbda59d02b8fc31c18aaa048cd7d901a.png)

Из них:
- успешных оказалось **26** кейсов → **52%**; 
- не прошли **24** тест-кейса → **48%**.

## При подключении к СУБД PostgreSQL

![image](https://i.gyazo.com/62557dea16dbc0f82db79eaf8b243bca.png)

Из них:
- успешных оказалось **26** кейсов → **52%**; 
- не прошли **24** тест-кейса → **48%**.

------------

## UI-тесты
- Позитивных тест-кейсов: **4** (HappyPath1 и 2);
- Негативных: **46** (FieldNumberTests, FieldMonthTests, FieldYearTests, FieldOwnerTests, FieldCVVTests).

**Результаты тестов, MySQL**

![image](https://i.gyazo.com/5067d60f43921b22593b10ccaf316647.png)

**Результаты тестов, PostgreSQL**

![image](https://i.gyazo.com/340dd28e26b6c405bdb9bb198b6d4083.png)

------------

## API-тесты
Проведено 4 API-теста, все прошли **успешно**.

![image](https://i.gyazo.com/fb51ae7686176dd32ce978210766ebd8.png)

------------

## Рекомендации
1. Предусмотреть, чтобы в случае, когда какое-либо поле ввода остается пустым, — под ним появлялось сообщение об ошибке "Поле обязательно для заполнения". В данный момент же показывается сообщение "Неверный формат", что, на мой взгляд, несовсем корректно;
2. Для поля "Владелец" реализовать возможность вводить только латинские буквы;
3. Предусмотреть, чтобы кнопка "Продолжить" не была активной (на неё нельзя было нажать), если не заполнено какое-либо из полей или введены ошибочные данные;
4. Сделать так, что кнопки "Купить" и "Купить в кредит" меняли цвет в зависимости от того, какая форма активна (красный — активна, белый — неактивна), 
т.к. сейчас кнопка "Купить в кредит" всегда красная и это несколько сбивает, если переключаться на форму "Оплата по карте";
5. Исправить орфографическую ошибку в слове "Марракеш".

Подробнее о дефектах можно посмотреть в [**Issues**](https://github.com/Ramastix/QA-Diploma/issues).
