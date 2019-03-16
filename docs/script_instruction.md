# Инструкция по запуску скриптами.

**Шаг 1**

Клонируем себе этот репозиторий:
```bash
git clone https://github.com/ARtoriouSs/docker-ims.ostis.git
cd docker-ims.ostis
```

**Шаг 2**

Запускаем run.sh:
```bash
./run.sh /путь/к/папке/с/базой [noupdate]
```
/путь/к/папке/с/базой это относительный или абсолютный путь к папке где лежат все файлы которые должны быть в базе. Скорее всего это будет что-то типо ostis/kb. noupdate это необязательный аргумент, если он есть то будет использован докерфайл который не будет обновлять сабмодули системы, если его нет, то сабмодули обновятся. Их лучше обновлять, но иногда в репозитории остиса попадают изменения которые что-то ломают, если такое случилось, то можно использовать noupdate, скорее всего всё будет ок, но есть шанс что версия будет неактуальной.

Чтобы выключить тыкаем ctrl + C или ctrl + Z или просто закрываем терминал ~к хренам собачьим так ему!!1~.

Собсна это всё, вносим изменения в базу, и повторяем шаг 2 сколько влезет.

**Шаг 3**

Этот шаг можно выполнить в самом конце, он удалит все оставшиеся контейнеры. Он почти полностью выполняется в начале run.sh, так что при каждом новом запуске всё лишнее будет удаляться, но в самом конце можно сделать дополнительно:
```bash
./clean.sh
```

**Ну и для примера:**
```bash
./run.sh ../ostis/kb noupdate
```
запусткаем систему с базой из папки ../ostis/kb ничего не обновляя.

ctre + Z

```./run.sh ~/обитель_искусственного_интеллекта/Б@З@_ЗнАнИй``` запустит систему с базой из папки \~/обитель\_искусственного\_интеллекта/Б@З@\_ЗнАнИй обновив репозитории системы.

