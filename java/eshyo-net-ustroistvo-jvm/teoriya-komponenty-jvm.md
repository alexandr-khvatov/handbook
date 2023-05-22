# Теория: Компоненты JVM

## **Что такое виртуальная машина Java?**

**Виртуальная машина Java (JVM)** - это виртуальная симуляция физического компьютера, который выполняет скомпилированные программы Java (байт-код). JVM работает как приложение поверх операционной системы и предоставляет среду для Java-программ.

Поскольку они используют виртуальные машины, Java-программы не зависят от платформы и могут выполняться на разных аппаратных средствах и операционных системах в соответствии с принципом **WORA** (_Write Once Run Anywhere_).

Существует множество различных реализаций JVM. HotSpot-это основная эталонная реализация виртуальной машины Java. Он используется Oracle Java и OpenJDK.

Многие JVM (включая HotSpot) реализованы в соответствии со [спецификацией виртуальной машины Java](https://docs.oracle.com/javase/specs/jvms/se9/html/index.html). Вам не нужно читать его сейчас, просто помните, что эта спецификация существует.

## **Обзор внутренних компонентов JVM**

После компиляции Java-программы появляется файл с расширением **.class**. Он содержит байт-код Java. Чтобы выполнить код, вам нужно загрузить его в JVM. Когда JVM выполняет программу, она переводит байт-код в собственный код платформы.

JVM в основном выполняет следующие действия:

* загружает байт-код;
* проверяет байт-код;
* выполняет байт-код;
* предоставляет среду выполнения.

На следующем рисунке показана общая архитектура JVM:

<div align="center">

<img src="../.gitbook/assets/image (248).png" alt="">

</div>

## **Подсистема загрузчика классов**

Эта подсистема загружает байт-код Java для выполнения, проверяет его, а затем выделяет память для байт-кода. Мы рассмотрим подсистему в другой теме. Для проверки **байт-кода существует модуль bytecode verifier**. Он проверяет, что инструкции не требуют каких-либо опасных действий, таких как доступ к частным полям и методам классов и объектов.

## **Области данных среды выполнения**

Эта **подсистема** представляет **память JVM**. Области используются для различных целей во время выполнения программы.

* **PC register** содержит адрес текущей инструкции;
* **область стека**-это место памяти, где хранятся вызовы методов и локальные переменные;
* **собственный стек методов** хранит информацию о собственном методе;
* **в куче** хранятся все созданные объекты (экземпляры классов);
* **область методов** хранит всю информацию об уровне класса, такую как имя класса, имя непосредственного родительского класса, информацию о методе и все статические переменные.

Каждый поток имеет свой собственный **регистр ПК**, **стек**и **собственный стек методов**, но все потоки используют одну и ту же **кучу** и **область методов.**

## **Механизм выполнения**

Он отвечает за выполнение программы (байт-код). Он взаимодействует с различными областями данных JVM при выполнении байт-кода.

Механизм выполнения состоит из следующих частей:

* **интерпретатор байт**-кода интерпретирует байт-код построчно и выполняет его (довольно медленно);
* **just-in-time compiler** (JIT-компилятор) переводит байт-код на родной машинный язык во время выполнения программы (он выполняет программу быстрее, чем интерпретатор);
* **сборщик мусора** очищает неиспользуемые объекты из кучи.

Различные реализации JVM могут содержать как интерпретатор **байт**-кода, так и **компилятор just-in-time**или только один из них. Не путайте их с javac (source code to bytecode compiler); он не включен в JVM.

## Другие важные части JVM для выполнения:

* **native method interface** обеспечивает интерфейс между Java-кодом и библиотеками native method;
* **библиотека собственных методов** состоит из файлов (C/C++), которые необходимы для выполнения собственного кода.

Таким образом, JVM имеет много частей. Мы не будем рассматривать их все, потому что этого достаточно, чтобы понять JVM в целом. Принципы работы загрузчика классов и алгоритмы сборки мусора будут рассмотрены в отдельных разделах.