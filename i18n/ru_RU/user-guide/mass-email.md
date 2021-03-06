# Массовая рассылка 

## Как создать массовую рассылку

Вам необходимо иметь как минимум один целевой список с целевыми записями и шаблоном электронной почты в вашем crm.

1. Создайте новую кампанию со статусом `Email` или `Newsletter`. Выберите один или несколько целевых списков в поле `Целевые списки`.
2. После создания записи кампании, вам необходимо создать электронную почту для этой кампании: нажмите «плюс» на панели «Массовая рассылка». Укажите _Date Start_ - при отправке писем и выберите _Email Template_. Убедитесь в том, что _Status_ установлен как `Pending`.

Если все настроено правильно, электронные письма должны отправиться. Они должны отправляться частично каждый час (вы можете изменить размер порции в Администрировании > Исходящие письма). Администратор может изменить его, обновив поле `Планирование` в `Запланированном задании проверки учетных записей электронной почты`.

Вы можете проверить, отправлены ли электронные письма или нет в панели журнала

## Тестирование функции массовой рассылки

Нажмите правую раскрывающуюся папку в строке массовой рассылки в панели _Mass Email_, а затем щелкните _Send Test_.

## Журнал

В журнале вы можете увидеть:
* Отправлено ли письмо;
* Письма, открытые получателем;
* Ссылки, кликнутые получателем;
* Получатели, которые отказались;
* Возвращенные письма (не доставленные получателю).

## Отказ от массовой рассылки

По умолчанию система добавит отказ всем отправленным письмам. Но вы можете использовать личный шаблон.

Например:
```html
<a href="{optOutUrl}">Unsubscribe from the mailing list.</a>
```

Администратор может отключить обязательную отменную связь, добавляемую системой в разделе «Администрирование» > «Исходящие письма».

## Отслеживание URL

Если вы хотите знать, что ваш получатель открыл ссылку с вашего письма, вам нужно создать URL отслеживание. Укажите любые _Name_ и _URL_, к которым должна привести ваша ссылка. Затем вам нужно вставить сгенерированный код в свой шаблон электронной почты.

 Пример:
 ```html
<a href="{trackingUrl:55f2c87b09a220a78}">Try our demo</a>
 ```
 
## Целевые списки

Целевые списки содержат списки учетных записей, контактов, руководств и пользователей.

Пользователи могут заполнять целевые списки вручную, используя действие _Select_ на соответствующей панели, подробнее в «Списке целей». Существует возможность сделать фильтрацию, а затем выбрать все результаты поиска.

## Записи в целевых списках

Функция [Reports](reports.md#syncing-with-target-lists) обеспечивает возможность заполнения целевых списков записями, соответствующими определенным критериям.

## Исключение из целевых списков

Укажите исключение целевых списков, чтобы избежать отправки массовой почты определенным получателям. Если есть запись с адресом электронной почты, которая соответствует адресу электронной почты любой исключающей записи, первая запись также будет исключена.

## Журнал кампании

В Журнале кампании вы можете видеть электронные письма, которые были отправлены, открытые электронные письма, отсканированные электронные письма, пользователи которые отказались, и кто нажал ссылку в письме. Этот журнал можно использовать, создав целевой список (раскрывающийся список в правом верхнем углу панели) на основе записей из журнала. Например, вы выбираете только контакты, которые щелкали по ссылке (URL-адрес отслеживания).

## Исправление проблем

_Для администратора_

#### Что делать, если электронные письма не отправляются.

1. Проверьте, работает ли _Send Test_. Если не работает, проверьте правильность настроек SMTP.
2. Проверьте, установлен ли cron для вашей системы.
3. Проверьте, есть ли задание `Отправить массовую рассылку` и статус `Активный` (Администрирование > Запланированные задания > Отправить массовую рассылку). Проверьте, есть ли записи в журнале.

#### Что делать, если отслеживание URP имеет неправильный url-адрес, который не указывает на ваш crm.

Проверьте параметр 'siteUrl' в файле `data/config.php`. Он должен быть установлен как URL вашего EspoCRM, доступного из внешнего мира.

#### Отправленные письма не регистрируются

Отправленные электронные письма могут обрабатываться только с помощью учетной записью группы. Убедитесь, что у вас есть учетная запись электронной почты группы, которая отслеживает отправку сообщений электронной почты, отправленных в почтовый ящик.

Кроме того, некоторые поставщики почтовых серверов могут отклоняться от стандартов, поэтому отклоненные электронные письма не могут различаться.
