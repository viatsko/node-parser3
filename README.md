# node-parser3

[![Join the chat at https://gitter.im/dwr/node-parser3](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/dwr/node-parser3?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

<img src="node-parser3.png" />

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

Из-за особенностей Parser'а проект содержит fork node-библиотеки gateway (см. [lib/gateway.js](lib/gateway.js)).

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
