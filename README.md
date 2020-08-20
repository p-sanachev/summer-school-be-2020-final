# Итоговое задание летний школы 2020. Направление Backend
## Summary: 
Необходимо разработать систему “Торговая площадка продажи игровых ключей”.

В рамках данной системы, торговая площадка выступает в качестве посредника между покупателем и продавцом, за что берет процент с каждой торговой операции. 
Процент отчисляется с суммы продажи, к примеру: покупатель оплачивает 100% стоимости товара, продавец получает 95%, на баланс площадки начисляется 5%.  
Процент комиссии может настраиваться. 

## Определения: 
Игровой ключ - некоторая уникальная цифро-буквенная комбинация

Комиссия - процент с продажи товара, который начисляется на баланс торговой площадки.

Покупатель - человек, желающий купить игровой ключ для определенной игровой площадки (steam/gog/playstation etc.)

Продавец - человек, получивший ключи на определенной игровой площадке и желающий продавать их через данную систему.

Товар - игровые ключи к определенной игре, выставленные на продажу за определенную стоимость. Товар доступен к покупке, пока доступны ключи. При каждой успешной покупке, один из ключей отдается пользователю и недоступен больше для продажи.

Платежная сессия - информация о покупателе, сумме оплаты и выбранном товаре.

## Описание системы с точки зрения продавца:
При желании начать продавать ключи, продавец должен создать новый товар, введя данные об игре, стоимость игры (для простоты полагаем, что валюта одна) и загрузив игровые ключи. После этого товар появляется в общем списке доступны к покупке товаров. 

При продаже игрового ключа, продавец получается оповещение о продаже - некоторое сообщение на его веб-сервер, в котором содержится информация о купленном ключе, о покупателе, об оплате, о коммиссии и некоторый хэш, который позволяет провалидировать, что оповещение пришло от торговой площадки, а не от злоумышленника. Получение оповещения продавцом должно быть гарантированным, то есть должен быть механизм переоповещения в случае неудачи.

## Описание системы с точки зрения покупателя:
При желании купить ключ к какой-либо игре на какой-либо платформе, покупатель должен зайти на торговую площадку, выбрать нужную игру и оплатить. В качестве платежного средства используется банковская карта. Номер карты должен проверяться по алгоритму Луна (упрощенному). Валидные номера должны имитировать успешную оплату, невалидные — возвращать ошибку. 

После успешной оплаты, пользователь получает ключ на свою почту.

## Процесс оплаты:
Для начала оплаты необходимо передать информацию о товаре, email покупателя и сумму покупки. В ответ, получается некоторый идентификатор платежной сессии, который нужен для оплаты -- передачи данных банковской карты и идентификатора платежной сессии.

## Итоговый результат:
- Json API (REST, GraphQL другое)
- Выложено на сервер (сервис доступен по ip или url)
- Есть возможность выставить товар на продажу
- Есть возможность купить товар
- Есть Readme с описанием работы и описанием запуска
- Есть Сваггер-спецификация для методов с успешными и неуспешны примерами
