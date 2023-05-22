# Введение

![](<../../.gitbook/assets/image (69).png>)

## FALSE SHARING

**False sharing** в многопотоковом приложении, когда в одном блоке оказываются переменные модифицируемые из разных потоков, ведет к снижению производительности и увеличению нагрузки на Cache coherence механизмы. Подробно о том как это происходит, можно прочесть в [статье](http://habrahabr.ru/company/intel/blog/143446/) на эту тему.

![](<../../.gitbook/assets/image (161).png>)

## MEMORY PADDING

![](<../../.gitbook/assets/image (18).png>)
