# Задача «Артемий слишком занят»

Перед выполнением задания внимательно прочитайте:

- [О всех этапах проверки задания](https://github.com/urfu-2017/guides/blob/master/workflow/overall.md)
- [Как отправить пулл](https://github.com/urfu-2017/guides/blob/master/workflow/pull.md)
- [Как пройти тесты](https://github.com/urfu-2017/guides/blob/master/workflow/test.md)
- Правила оформления [javascript](https://github.com/urfu-2017/guides/blob/master/codestyle/js.md), [HTML](https://github.com/urfu-2017/guides/blob/master/codestyle/html.md) и [CSS](https://github.com/urfu-2017/guides/blob/master/codestyle/css.md) кода

## Основное задание
Билли отправляется в путешествие и ему хочется составить список мест,
которые он желает посетить. Но память постоянно подводит Билли,
и он забывает, в каких местах ему уже довелось побывать. Чтобы путешествие Билли было
увлекательным, и он посетил запланированные достопримечательности, ему нужен сервис для сохранения и просмотра отметок о посещенных местах.

Билли прочитал хорошую книгу по фронтенду и сделает его сам,
а своего друга, опытного путешественника Артемия, попросил реализовать REST-интерфейс (API), используя Express.
Но Артемий укатил в очередную экспедицию, и просит помощи у вас.

### Билли просил
- Возможность добавления нового места (страны, города, достопримечательности)
    - Место состоит из описания и отметки о посещении
    - Место создается непосещённым
- Возможность получения списка мест
    - Можно сортировать по дате создания
    - Можно сортировать по алфавиту
    - Можно выводить список мест постранично
- Возможность поиска места по его описанию
- Возможность редактирования описания конкретного места
- Возможность отметить место посещённым или непосещённым
- Возможность удаления места
- Возможность менять порядок мест в списке
- Возможность очистки всего списка мест

#### Перед запуском укажите AUTH_TOKEN и PORT в .env файле.
##### Каждый запрос должен содержать в headers ключ Authorization с токеном

#### Посмотреть специфику модели Location
- **OPTIONS** */locations*
   
#### Получение списка мест
- **GET** */locations*
    - Параметры (в порядке применения):
        - sortBy
        - limit / offset
        - select / query
        - reverse
    - Пример запроса:
        - */locations?select=description&query=текст&sortBy=title&reverse=true&limit=10&offset=10*
#### Очистить список мест:
- **DELETE** */locations*
#### Добавление нового места
- **PUT** */locations* (body raw json / x-www-form-urlencoded)
```javascript
{
  "type": "2",
  "title": "Awesome place"
}
```
#### Получение места:
- **GET** */locations/{uuid}*
#### Обновление места:
- **PATCH** */locations/{uuid}* (body raw json / x-www-form-urlencoded)
#### Удаление места:
- **DELETE** */locations/{uuid}*
#### Поменять порядок двух мест
- **PATCH** */locations?swap=***{firstOrder}**,**{secondOrder}**
    
![artemii](https://user-images.githubusercontent.com/8963033/37154087-b5f1ed76-2300-11e8-81b7-0a8700bc5f57.png)
