B4CKSP4CE
======
Сайт-вики Бэкспейса.

## Как добавить эвент?
В папке `_events` создать .md-файл с названием будущей страницы эвента, в начало этого файла добавить метаданные:
```md
---

layout: event
title: Мастер-класс «Как войти в разработку под zx-spectrum»
date: 07.12.2019 16:00

---
```

Помимо вышеперечисленных обязательных метаданных, есть ещё дополнительные поля, которые при заполнении генерируют более полный Rich Content объект для поисковиков:
```
event_description: Описание эвента для поисковых движков 
end_date: 07.12.2019 18:00
```

При этом, в контент страницы не нужно добавлять ни дату, ни заголовок — в шаблоне они уже добавлены. Получается, что идеальный пост выглядит примерно так:
```md
---

layout: event
title: Мастер-класс «Как войти в разработку под zx-spectrum»
date: 07.12.2019 16:00
event_description: На семинаре Петр (errorsoft) расскажет как настроить окружение для разработки под Спектрум (ассемблер, редактор, эмулятор), про структуру памяти и научит участников создавать простые атрибутные эффекты.
end_date: 07.12.2019 18:00

---
Сообщества Embedded и ChaosConstructions открывают серию семинаров, посвященных демосцене — полностью некоммерческому и соревновательному, спортивному виду искусства, позволяющему делать яркие и красивые спецэффекты в ограниченных вычислительных ресурсах.

На первом семинаре "Как войти в разработку под ZX-Spectrum"  Петр aka [errorsoft](https://github.com/errorcalc) расскажет как настроить окружение для разработки под Спектрум (ассемблер, редактор, эмулятор), про структуру памяти и научит участников создавать простые атрибутные эффекты.
```

Если всё заполнено правильно, то Jekyll сам добавит событие в каталог событий (/events) в нужный год и месяц.

## Как собрать и протестировать это локально? 
Всё завязано на гем [github/pages-gem](https://github.com/github/pages-gem), можно его поставить на хост-машину, но в репозитории лежит готовый Dockerfile, который всё сделает за вас в контейнере, чтобы не мусорить лишний раз.

```bash
git pull https://github.com/b4ck5p4c3/0x08.in
cd 0x08.in
docker build . -t b4cksp4ce/ghpages
docker run --rm -p 8080:4000 -v `pwd`:/jekyll b4cksp4ce/ghpages
```

Сайт будет доступен по адресу http://localhost:8080/
