Домашнее задание
================
Практическое задание по курсу Параллельное Программирование на кафедре ВМ, факультета ЕН, 2016 год.
Синхронизация с помощью блокировки.

Необходимое ПО
--------------
1. Java SDK 7 или более поздняя:
   http://www.oracle.com/technetwork/java/javase/downloads/index.html

2. Apache Maven 3.x:
   http://maven.apache.org/download.cgi

Описание
--------
Задание включает в себя следующие основные исходные файлы:

* src/main/java/ru/ifmo/pp/fgb/Bank.java содержит интерфейс для гипотетического
  банка с набором операций getNumberOfAccounts, getAmount, getTotalAmount, deposit, withdraw, transfer.

* src/main/java/ru/ifmo/pp/fgb/BankImpl.java содержит реализацию операций банка для
  однопоточного случая. Реализация небезопасна для использования из нескольких потоков одновременно.

* pom.xml содержит описание проекта для системы сборки Maven. Используейте его, чтобы создать проект в вашей
  любимой среде разработки. Рекомендуется IntelliJ IDEA. Используя операцию File | Import Project... и указав
  месторасположение файла pom.xml, вы создадите проект для выполнения задания.

Задание
-------
1. Необходимо доработать реализацию BackImpl так, чтобы она стала безопасной для использования из множества
   потоков одновременно.

2. Для реализации необходимо использовать тонкую блокировку. Синхронизация должна осуществляться для
   каждого счета по отдельности. Добавьте поле lock типа java.util.concurrent.locks.Lock (инерфейс для примитива
   блокировки) в класс BankImpl.Account и используйте класс java.util.concurrent.locks.ReentrantLock в качестве
   стандартной реализации.

3. Для обеспечения линеаризуемости операций должна использоваться двухфазная блокировка всех операций.

4. Для избежания ситуации взаимной блокировки (deadlock) необходимо использовать иерархическую блокировку.

5. Код должен быть отформатирован в сотвеетсвевии со стандартным Java стилем используя 4 пробела для выравнивания
   кода. Следуйте стилю, в котором написаны классы Bank и BankImpl. Плохо отформатированный код не будет проверяться.

Сборка и тестирование
---------------------
Проект должен собираться и успешно проходить тестирование с помощью команды "mvn test".
При этом автомически будут запущены сделующе тесты:

* src/test/java/ru/ifmo/pp/fgb/FunctionalTest.java проверяет базовую корректность работы операций банка.

* src/test/java/ru/ifmo/pp/fgb/MultiThreadTest.java проверяет основные аспекты корректности работы банка при
  множестве одновременно работающих потоков исполнения.

Для запуска тестов из IntelliJ IDEA откройте файл с тестом (используйте Сtrl+N для поиска класса по имени) и
запускайте его или отдельный тесты на исполнение с помощью комбинации Ctrl+Shift+F10.

Обратите внимание, что прилагаемая реализация проходит только FunctionalTest, но не проходит MultiThreadTest.

Порядок сдачи
-------------
1. Сдавать задание нужно в виде форка и пулл-реквеста к https://github.com/ITMO-ENF-MT-2016/hw1,
   в описании укажите ФИО и номер группы.
   Подробнее про пулл-реквесты можно почитать тут:
   http://habrahabr.ru/post/125999/ и https://help.github.com/articles/using-pull-requests.

2. Если задание выполнено неверно, то это будет написано в комментариях к пулл-реквесту.
   Сдавать задание на проверку можно несколько раз.

3. После того, как будет сдано верное решение, его нужно защитить во время практического занятия.
   В рамках защиты будет задано несколько вопросов по вашему коду.

Оценки
------
https://docs.google.com/spreadsheets/d/16GHoTqEzEIGRbedos-nUAFBvQL_c3w3NO1V72MK69Z0/edit?usp=sharing
