# Race Condition | Data Races

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

## Data Races

Ситуация когда, несколько потоков пытаются обратиться к одной области памяти, и по крайней мере один из потоков пишет в переменную без синхронизации.

Например одновременное обновление переменной и если в случае int такая операция атомарна, возможно значение перезапишется несколько раз, то в случае long, double могут возникнуть потери данных для 32bit процессоров.

![](<../.gitbook/assets/image (129).png>)

![](<../.gitbook/assets/image (395).png>)

## Race Condition

Ситуация когда НЕСКОЛЬКО потоков получают доступ к shared variable.  А ее значение будет зависеть от порядка выполнения операций в потоках.

2 причины:

1. &#x20;Проверка и обновление Check and update
2. Чтение и обновление Read and update

### Check and update

![](<../.gitbook/assets/image (145).png>)

![](<../.gitbook/assets/image (13).png>)

![](<../.gitbook/assets/image (130).png>)

![](<../.gitbook/assets/image (378).png>)

### РЕШЕНИЕ

![](<../.gitbook/assets/image (83).png>)

![](<../.gitbook/assets/image (369).png>)

![](<../.gitbook/assets/image (121).png>)

### Read and update

![](<../.gitbook/assets/image (415).png>)

![](<../.gitbook/assets/image (58).png>)

### РЕШЕНИЕ

![](<../.gitbook/assets/image (255).png>)

![](<../.gitbook/assets/image (326).png>)

## Conclusion

![](<../.gitbook/assets/image (350).png>)
