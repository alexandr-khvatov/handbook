# Метод и функция

Функция - не изменяет данные, а возвращает новые.

Метод - производит изменения. (Например setter изменяет значения поля)

Следовательно, существуют следующие различия между концепцией\
методов и чистыми функциями:

|                |                                            Метод                                           |                                                              Чистая функция                                                              |
| -------------- | :----------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------: |
| Мутация        |   Метод _мутирует_, т. е. изменяет данные и вызывает другие изменения и побочные эффекты.  | <p>Чистая функция <em>не</em><br><em>мутирует</em>, т. е. она просто проверяет<br>данные и выдает результаты в<br>виде новых данных.</p> |
| Как и что      |                   <p>Методы описывают, <em>как</em><br>все делается.</p>                   |                        <p>Чистые функции описывают то, <em>что</em><br>делается, а не то, как это<br>делается.</p>                       |
| Порядок вызова | <p>Методы используются<br><em>императивно</em>, т. е.<br>имеет значение порядок вызова</p> |                  <p>Чистые функции используются<br><em>декларативно</em>; т. е. порядок<br>вызова не имеет значения</p>                  |
| Код и данные   |        <p>Методы являются <em>кодом</em>, т. е. они<br>вызываются и выполняются</p>        |          <p>Функции являются <em>кодом как данные</em>;<br>т. е. они не только<br>исполняемы, но и<br>передаются как данные.</p>         |

