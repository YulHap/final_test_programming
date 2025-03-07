# Итоговая контрольная работа

## Информация о проекте
Необходимо организовать систему учета для питомника в котором живут
домашние и вьючные животные.

## Как сдавать проект
Для сдачи проекта необходимо создать отдельный общедоступный
репозиторий(Github, gitlub, или Bitbucket). Разработку вести в этом
репозитории, использовать пул реквесты на изменения. Программа должна
запускаться и работать, ошибок при выполнении программы быть не должно.
Программа, может использоваться в различных системах, поэтому необходимо
разработать класс в виде конструктора

## Задание
1. Используя команду cat в терминале операционной системы Linux, создать
два фала Домашние животные (заполнив файл собаками, кошками,
хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и
ослы), а затем объединить их. Просмотреть содержимое созданного фала.
Переименовать фал, дав ему новое имя (Друзья человека).

```sh
cat > 'Домашние животные'
Собаки
Кошки
Хомяки
```


```sh
cat 'Вьючные животные'
Лошади
Верблюды
Ослы
```


```sh
 cat 'Домашние животные' 'Вьючные животные' > 'Домашние и вьючные животные'
```

```sh
 cat 'Домашние и вьючные животные'
Собаки
Кошки
Хомяки
Лошади
Верблюды
Ослы
```

```sh
mv 'Домашние и вьючные животные' 'Друзья человека'
```

2. Создать директорию, переместить файл туда.

```sh
mkdir 'Животные в питомнике'
```

```sh
mv 'Друзья человека' 'Животные в питомнике'
```

3. Подключить дополнительный репозиторий MySQL. Установить любой пакет
из этого репозитория.

```sh
apt install mysql-server-8.0
```

4. Установить и удалить deb-пакет с помощью dpkg.

Заходим на сайт VirtualBox и переходим на страницу для загрузки VirtualBox (https://www.virtualbox.org/wiki/Downloads).
Выбираем там нужную платформу *Linux distributions*.
Кликаем правой кнопкой мыши по ​Ubuntu 22.04 и выбираем "Копировать адрес ссылки".
Так мы скопировали адрес ссылки deb-пакета.
Переходим в терминал Linux и скачиваем файл по скопированной ссылкe
```sh
wget https://download.virtualbox.org/virtualbox/7.1.6/virtualbox-7.1_7.1.6-167084~Ubuntu~jammy_amd64.deb
```

После того как пакет скачался, нам нужно установить этот пакет
```sh
dpkg -i virtualbox-7.1_7.1.6-167084~Ubuntu~jammy_amd64.deb
```

Пакет не устанавливается, потому что нет необходимых зависимостей.
Для установки всех зависимостей и установки нашего пакета запустим команду 

```sh
apt -f install
```
Эта команда восстанавливает нарушенные зависимости и автоматически исправляет ошибки при установке пакетов.
Пакет установлен.

Для удаления пакета используем команду 
```sh
dpkg -r virtualbox-7.1
```
и удалим все зависимости

```sh
 apt autoremove
```

5. Выложить историю команд в терминале ubuntu

Чтобы вывести все команды, которые были запущены в терминале Ubuntu, нужно запустить команду

```sh
history
```

6. Нарисовать диаграмму, в которой есть класс родительский класс, домашние
животные и вьючные животные, в составы которых в случае домашних
животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные
войдут: Лошади, верблюды и ослы).

7. В подключенном MySQL репозитории создать базу данных “Друзья
человека”

В терминале Linux захожу в mysql-server
```sh 
mysql
```

Создаю нового пользователя с именем jul_finaltest и паролем 123456
```sh
CREATE USER 'jul_finaltest'@'localhost' IDENTIFIED BY '123456';
```
Передам данному пользователю все права на все базы данных

```sh
GRANT ALL PRIVILEGES ON *.* TO 'jul_finaltest'@'localhost' WITH GRANT OPTION;
```

Применяю изменения
```sh
FLUSH PRIVILEGES;
```

Выхожу из mysql-server
```sh
exit
```
И захожу в mysql-server обратно уже под новым пользователем jul_finaltest с паролем
```sh
mysql -u jul_finaltest -p
```
Ввожу пароль по запросу и попадаю в mysql-server.

Новый пользователь с паролем создан для того, чтобы я могла заходить в БД не только через терминал Linux с правами root, но и другими способами входа в БД.

Создаю новую базу данных "Друзья человека"
```sh
CREATE DATABASE Friends_of_man; 
```

8. Создать таблицы с иерархией из диаграммы в БД
9. Заполнить низкоуровневые таблицы именами(животных), командами
которые они выполняют и датами рождения
10. Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой
питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу.
11. Создать новую таблицу “молодые животные” в которую попадут все
животные старше 1 года, но младше 3 лет и в отдельном столбце с точностью
до месяца подсчитать возраст животных в новой таблице
12. Объединить все таблицы в одну, при этом сохраняя поля, указывающие на
прошлую принадлежность к старым таблицам.
13. Создать класс с Инкапсуляцией методов и наследованием по диаграмме.

14. Написать программу, имитирующую работу реестра домашних животных.
В программе должен быть реализован следующий функционал:
 
 Завести новое животное
 * определять животное в правильный класс
 * увидеть список команд, которое выполняет животное
 * обучить животное новым командам
 * Реализовать навигацию по меню

15. Создате класс Счетчик, у которого есть метод add(), увеличивающий̆
значение внутренней̆int переменной̆на 1 при нажатие “Завести новое
животное” Сделайте так, чтобы с объектом такого типа можно было работать в
блоке try-with-resources. Нужно бросить исключение, если работа с объектом
типа счетчик была не в ресурсном try и/или ресурс остался открыт. Значение
считать в ресурсе try, если при заведения животного заполнены все поля.
