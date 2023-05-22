# Процесс и поток

<mark style="color:green;">Процесс — экземпляр программы во время выполнения</mark>, независимый объект, которому выделены системные ресурсы (например, процессорное время и память). <mark style="color:green;">Каждый процесс выполняется в отдельном адресном пространстве: один процесс не может получить доступ к переменным и структурам данных другого.</mark> Если процесс хочет получить доступ к чужим ресурсам, необходимо использовать межпроцессное взаимодействие. Это могут быть конвейеры, файлы, каналы связи между компьютерами и многое другое.

<mark style="color:blue;">Поток использует то же самое пространства стека, что и процесс, а множество потоков совместно используют данные своих состояний.</mark> Как правило, каждый поток может работать (читать и писать) с одной и той же областью памяти, в отличие от процессов, которые не могут просто так получить доступ к памяти другого процесса. У каждого потока есть собственные регистры и собственный стек, но другие потоки могут их использовать.

<mark style="color:blue;">Поток — определенный способ выполнения процесса. Процесс всегда имеет хотя бы один (главный) поток.</mark> Когда один поток изменяет ресурс процесса, это изменение сразу же становится видно другим потокам этого процесса.