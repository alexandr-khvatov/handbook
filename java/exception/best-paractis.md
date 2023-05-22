# best paractis

![](<../.gitbook/assets/image (435).png>)

![](<../.gitbook/assets/image (279).png>)

![](<../.gitbook/assets/image (212).png>)

![](<../.gitbook/assets/image (119).png>)

![](<../.gitbook/assets/image (352).png>)

![](<../.gitbook/assets/image (399).png>)

![](<../.gitbook/assets/image (354).png>)

![](<../.gitbook/assets/image (249).png>)

![](<../.gitbook/assets/image (442).png>)

finally выполняется непосредственно перед возвратом из метода, а не перед выполнение оператора return

когда исполнитель java видит " return x; " он вычисляет " x " результат фиксируется, после этого перед выполнением return передаем управление finally, и то что в finally имеется выражение " x = 6; " оно не имеет роли для return, т.к в return уже вычислено выражение:

![](<../.gitbook/assets/image (417).png>)
