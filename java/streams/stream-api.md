---
description: java.util.stream
---

# Stream API

Коллекции - это как "склад", у них есть методы size(), contains(), т.е. как - бы ведется учёт на "складе", Stream же  - это поток, который возникает из чего - то, например можно прикрутить на Socket, генератор, коллекции. Из Stream можно только брать элементы, это позволяет делать ленивые вычисления (вычисления выполняются только на терминальной операции).

Иногда не понимают зачем нужен Stream, если есть Коллекции:

Stream - это более абстрактная штука, в том смысле что коллекции чаще всего представляют собой физическое хранилище, например, в памяти,  - данные где-то присутствую, а Stream создает поток данных, хотя и из коллекций можно создать Stream, но сам Stream не является хранилищем данных, он является интерфейсом к источнику данных, а а каким образом источник будет получать данные - брать их из хранилища или генерировать - Stream это абстрагирует.&#x20;

Важный момент Stream в отличии от коллекций не даёт изменить источник. Даже если Stream взят от изменяемой Коллекции.  Если Вы кому-то отдаете Stream, можете быть уверенными, что пользователь  не получит доступа на изменение к источнику Stream.

Важная особенность - Stream ленивый.

![](<../.gitbook/assets/image (446).png>)