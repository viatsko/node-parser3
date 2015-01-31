# node-parser3

Пример хостинга проекта на Parser 3 на node web-сервере.

В cgi/ находится бинарник Parser 3 для Mac OS X, если вам нужен другой - просто замените.

Установка зависимостей проекта (для работы рекомендуется node js v 0.10+):

```
npm install
```

Запуск проекта:

```
npm start
```

Из-за особенностей Parser'а проект содержит fork node-библиотеки gateway (см. ./lib/gateway.js).

Смена расширения файлов или маппинга на другой cgi-процесс производится в app.js изменением параметров gateway middleware:

```js
app.use(gateway(path.resolve('./public'), {
  '.html': path.resolve('./cgi/parser3.cgi')
}));
```

Если middleware планируется использовать с imprimatur1, то нужно добавить соответствующую опцию (по сути опция эмулирует RewriteEngine-директиву на передачу управления основному скрипту):

```js
app.use(gateway(path.resolve('./public'), {
  '.html': path.resolve('./cgi/parser3.cgi'),
  imprimatur: true
}));
```
