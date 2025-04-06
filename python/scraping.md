# Web scraping
> Автоматизация процесса извлечения информации из интернета

## [Правовой аспект](https://ipcmagazine.ru/articles/1729150/)
> `https://[domain]/robots.txt` - информация о запрете на использования скраппинга на сайте

## Инструменты для парсинга:
- Developer tools в браузере - панель разработчика
- Requests - библиотека запросов
- [Beautiful Soup](https://pypi.org/project/beautifulsoup4/) - работа с html-разметкой
- Requests-html - надстройка Requests для получения динамиеских данных
- Selenium - библиотека для парсинга и тестирование сайта

Парсинг на примере сайта [https://www.iplocation.net/](https://www.iplocation.net/):
```bash
pip install requests # библиотека запросов
pip install beautifulsoup4 # библиотека парсинга
pip install fake-headers # созданрие фейковых заголовков для запросов
pip install lxml # движок для работы bs4

```
```py
# /iplocation.py
import requests
from fake_headers import Headers
from bs4 import BeautifulSoup

headers = Headers(browser='firefox', os='win')
html_data = requests.get('https://www.iplocation.net/', headers=headers.generate()).text
soup = BeautifulSoup(html_data, 'lxml')

tag_div = soup.get('div', id='element_id')
tag_p = tag_div.findall('p')[0]
tag_span = tag_p.findall('span')[0]

print(tag_span.text)
```
