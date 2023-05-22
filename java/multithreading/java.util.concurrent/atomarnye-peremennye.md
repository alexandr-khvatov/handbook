# Атомарные переменные

![](<../../.gitbook/assets/image (124).png>)

## Пример: выполнить только 1 раз!

не сработает:

![](<../../.gitbook/assets/image (156).png>)

не лучшее решение:

![](<../../.gitbook/assets/image (205).png>)

![](<../../.gitbook/assets/image (295).png>)

сработает, т.к разделяемый ресурс - это переменная flag, а action не является разделяемым ресурсом, и  мы запоминаем что в секцию синхронизации зашли и флаг установили, в этом случае всё сработает, если мы устанавливали в текущем thread флаг устанавливали, иначе если в этом thread флаг не устанавливали, action не выполнится.

Но в таком решении имеется блок synchronized, который может дорого обходиться, и решение содержит много кода:

## хорошие решения

### 1

![](<../../.gitbook/assets/image (267).png>)

### 2

Производительней предыдущего решения, но читаемость гораздо меньше.

![](<../../.gitbook/assets/image (200).png>)

[https://lms-vault.s3.amazonaws.com/private/1/courses/2020-spring/nsk-java/slides/java\_lecture\_300420.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256\&X-Amz-Credential=AKIAUKOEY5ZX6VXK3RWN%2F20220223%2Feu-central-1%2Fs3%2Faws4\_request\&X-Amz-Date=20220223T094611Z\&X-Amz-Expires=10\&X-Amz-SignedHeaders=host\&X-Amz-Signature=dc95252b01912a23e36f830dbd5f9a9fcdefb5c16a4a46ff1b22a72dd535a2c0](https://lms-vault.s3.amazonaws.com/private/1/courses/2020-spring/nsk-java/slides/java\_lecture\_300420.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256\&X-Amz-Credential=AKIAUKOEY5ZX6VXK3RWN%2F20220223%2Feu-central-1%2Fs3%2Faws4\_request\&X-Amz-Date=20220223T094611Z\&X-Amz-Expires=10\&X-Amz-SignedHeaders=host\&X-Amz-Signature=dc95252b01912a23e36f830dbd5f9a9fcdefb5c16a4a46ff1b22a72dd535a2c0)
