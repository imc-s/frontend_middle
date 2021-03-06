**Тестовое задание для соискателя на должность frontend-разработчика уровня middle в компании ООО "ИМЦ".**

Реализовать генератор форм ввода данных.
Задание необходимо выполнить на фреймворке Vue (предпочтительнее на Vue 3.0).
На статичной форме размещены 2 компонента: многострочный текстовый редактор и кнопка.
Предоставить пользователю возможность описать в текстовом редакторе json-объект (пример объекта ниже) и нажать кнопку.
По нажатию на кнопку система должна интерпретировать json-объект, создать и визуализировать модальную форму, 
наполненную компонентами, описанными в json-объекте.

Структура json-объекта:
```
[
	{
		"type": "container"|"input"|"datepicker"|"list", 
		"code": уникальный ключ компонента в объекте для возможной последующей обработки 
		"parent": визуальный контейнер, на котором размещен компонент
		"listdata":[{"key":"value"}]
	}
]
```
где:
"type" - тип компонента на форме:
	container - визуальный контейнер, на котором может быть размещен другой компонент (должен быть изображен в виде рамки серого цвета)
	input - поле ввода строчных данных
	datepicker - компонент для ввода данных типа "дата"
	list - компонент списка выбора значений
	listdata - данные для наполнения компонента типа list
"parent" - ссылка на некий контейнер. Должна поддерживаться неограниченная вложенность компонентов в контейнеры. 
	Допускается размещение на визуальном контейнере других контейнеров.
	В одном контейнере могут быть одновременно размещены другие контейнеры и компоненты ввода данных.
	
Пример json-объекта, описывающего содержимое генерируемой модальной формы.	
```
[
  {
    "type": "container",
    "code": "k1",
    "parent": null
  },
  {
    "type": "input",
    "code": "c1",
    "parent": "k1"
  },
  {
    "type": "datepicker",
    "code": "c2",
    "parent": "k1"
  },
  {
    "type": "container",
    "code": "k2",
    "parent": "k1"
  },
  {
    "type": "list",
    "code": "с3",
    "parent": "k2",
    "listdata": [
      {
        "key": 1,
        "value": "мужской"
      },
      {
        "key": 2,
        "value": "женский"
      }
    ]
  },
  {
    "type": "input",
    "code": "c4",
    "parent": "k2"
  }
]
```

Дополнительным плюсом соискателю будет размещение на исходной статичной форме третьего компонента типа многострочный текстовый редактор,
в котором отобразится json-объект, содержащий данные, введенные пользователем в компоненты ввода на модальной форме.
Собирать и отображать этот json-объект можно, например, по закрытию модальной формы.

Результат выполнения задания следует оформить на github, где в README.md описать способ установки и проверки результата!
