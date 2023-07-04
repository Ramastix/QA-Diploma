# Дипломный проект по курсу «Тестировщик ПО»
## О проекте

Проект представляет собой комплексное автоматизированное тестирование сервиса по покупке туров через интернет-банк. Купить тур можно с помощью двух способов:
- оплата с помощью дебетовой карты
- покупка в кредит

Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:
- сервису платежей (Payment Gate)
- кредитному сервису (Credit Gate)

Приложение в собственной СУБД сохраняет информацию о том, каким способом был совершён платёж и успешно ли он был совершён.

## Документация

- [План автоматизации тестирования](https://github.com/Ramastix/QA-Diploma/blob/main/Plan.md)
- [Отчет по итогам тестирования](https://github.com/Ramastix/QA-Diploma/blob/main/Report.md)
- [Комплексный отчет по итогам всего процесса автоматизации](https://github.com/Ramastix/QA-Diploma/blob/main/Summary.md)

## **Перед началом работы**
1. Загрузите на свой ПК данный репозиторий. Для этого либо воспользуйтесь командой git clone и вставьте ссылку https://github.com/Ramastix/QA-Diploma .
2. Установите Docker Desktop или Docker Toolbox (в зависимости от вашей ОС). Ознакомьтесь с [этой](https://github.com/netology-code/aqa-homeworks/blob/aqa4/docker/installation.md) инструкцией.

## **Запуск**
1. **Запускаем docker-контейнер с СУБД MySQL и PostgreSQL, а также Node.js.**

Все параметры для запуска уже есть в соответствующем файле — docker-compose.yml. Вам необходимо лишь ввести в терминале команду:
```
docker-compose up
```

---------

2. **Запускаем SUT**

Для этого открываем новую вкладку в Терминале IDEA и вводим следующую команду:
```java
java -jar artifacts/aqa-shop.jar
```
- для СУБД **MySQL**:
```java
java -Dspring.datasource.url=jdbc:mysql://192.168.99.100:3306/app -jar artifacts/aqa-shop.jar
```
- для СУБД **PostgreSQL**:
```java
java -Dspring.datasource.url=jdbc:postgresql://192.168.99.100:5432/app -jar artifacts/aqa-shop.jar
```
Дожидаемся сообщения, которое будет означать готовность SUT к работе:
```java
ShopApplication  : Started ShopApplication 
```

В браузере сервис будет доступен по адресу http://localhost:8080/.

---------

3. **Запускаем авто-тесты**

Для этого открываем еще одну вкладку в Терминале и вводим следующую команду:
- для СУБД **MySQL**:
```java
gradlew clean test -Ddb.url=jdbc:mysql://192.168.99.100:3306/app 
```
- для СУБД **PostgreSQL**:
```java
gradlew clean test -Ddb.url=jdbc:postgresql://192.168.99.100:5432/app
```
---------

4. **Генерируем отчет Allure по итогам тестирования, который автоматически откроется в браузере**

Используем команду:
```java
gradlew allureServe
```
После просмотра отчета останавливаем действие allureServe комбинацией клавиш **Ctrl + C**, подтверждаем закрытие клавишей **Y** и нажимаем **Enter**.

## **Если возникла необходимость перезапустить тесты**
Если нужно перезапустить тесты, либо переподключить контейнер и SUT не выходя при этом из проекта, то во вкладках терминала с запущенным контейнером 
и SUT нажмите **CTRL + C**, соответственно и контейнер, и SUT прекратят свою работу. Затем опять включаем по очереди, вводя команды из п.1 и п.2.
