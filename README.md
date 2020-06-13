# Работа с Github

Перед началом работы делаем резервную копию проекта. 
Если вы уже начали работать с гитом, но что-то не получается, лучше начать с начала.

Инструкция проверена от начала и до конца и если в точности следовать тому, что здесь написано, у вас все получится.

## 1. Клонирование репозитория наставнка и создание своего

#### Данный пункт выполняем, если решили делать работу с gulp сборкой, если не используете gulp можете сразу переходить у пункту 1.1

Копируем адрес репозитория тип соединения не важен т.к. к моему репозиторию у вас доступа не будет. Но для своего репозитория о том как его настроить можете посмотреть тут https://youtu.be/MnU1U7GCWLk

![Alt text](https://portomebel.ru/upload/loft/1.png)

Открываем терминал и заходим в папку с проектом

Пишем (если хотим склонировать проект со сборкой):
```{r, engine='bash', count_lines}
git clone git@github.com:MaxOrel/BuilderBurger.git burger
```

После чего в папке, где вы сделали эту команду должны появиться папка со сборкой проекта

![Alt text](https://portomebel.ru/upload/loft/2.png)


### 1.1 Создаем свой удаленный репозиторий

Создаем новый репозиторий на github

![Alt text](https://portomebel.ru/upload/loft/3.png)

## 2. Работа с репозиторием на компьютере

### 2.1 Создаем связь с личным удаленным репозиторием
Открываем терминал и заходим в папку с проектом (папка в которой есть папка .git)

![Alt text](https://portomebel.ru/upload/loft/4.png)

Далее выполняем связь своего удаленного репозитория с этой папкой:
```{r, engine='bash', count_lines}
git remote add origin git@github.com:unosmart/burger.git
```
Где git@github.com:unosmart/burger.git - ваш репозиторий

После того как создали связь с личным репозиторием делаем команду
```{r, engine='bash', count_lines}
git push -u origin master
```
У Вас запросит название аккаунта и пароль (если не подключен ssh), после корректного ввода произойдет загрузка файлов в ваш удаленный репозиторий.

### 2.2 Создаем недельную ветку и начинаем разработку

Переходим в папку проекта и локально создаем новую ветку (напоминаю корнем вашего проекта будет папка в которой лежит папка .git, не путайтесь, если какие-то вопросы пишите мне в личку) 

```{r, engine='bash', count_lines}
git checkout -b week_1
```
![Alt text](https://portomebel.ru/upload/loft/6.png)

Работаем в этой ветке (вставляем файлы из сохраненной папки в сборку то, что вы уже сверстали или сделали или пишем с нуля если ничего не делали)

Изменяем readme.md файл используя MARKDOWN разметку: указываем в нем
* Свое ФИО
* Имя наставника
* Название курса

![Alt text](https://portomebel.ru/upload/loft/7.png)

После делаем, только всегда смотрите в какой ветке вы находитесь в данном случае мы пока в week_1

```{r, engine='bash', count_lines}
git add .
git commit -m "Текст коммита"
```

![Alt text](https://portomebel.ru/upload/loft/8.png)

Коммит создан

Делаем push изменений в удаленный репозиторий (ВНИМАТЕЛЬНО мы делаем пуш уже не в ветку MASTER, а в ветку week_1 она автоматически создаться в вашем личном удаленном репозитории если ее там нет)

```{r, engine='bash', count_lines}
git push -u origin week_1
```

![Alt text](https://portomebel.ru/upload/loft/9.png)

## 3. Проверка работы и сдача работы наставнику

Для того чтобы показать работу настанику ее необходимо отобразить либо на хостинге, либо на Github Pages. Второй вариант предпочтительнее.

Создаем новую ветку (ВАЖНО ветку создаем на удаленном репозитории и находиться нужно на ветке week_1) на github называем ее gh-pages

![Alt text](https://portomebel.ru/upload/loft/10.png)
![Alt text](https://portomebel.ru/upload/loft/11.png)

Заходим с настройки репозитория 
1. Переходим на вкладку settings
2. Выбираем ветку gh-pages. Нажимаем save

![Alt text](https://portomebel.ru/upload/loft/12.png)

Создаем pull request из week_1 в master
![Alt text](https://portomebel.ru/upload/loft/13.png)
![Alt text](https://portomebel.ru/upload/loft/14.png)

### Публикуем изменения на github pages ###

После того как мы поработали локально в недельной ветке, т.е. например вы что-то доработали или исправили и хотите сдать мне на проверку в консоли пишем 

(Это если у вас локально что-то изменилось)
```{r, engine='bash', count_lines}
git push origin week_1
```
Потом обновляем то что в ветке gh-pages на удаленном.
```{r, engine='bash', count_lines}
git push origin week_1
git push origin week_1:gh-pages
```
*week_1 заменяем на текущую недельную ветку*. Таким образом все актуальные изменения мы заливаем на gh-pages и они будут доступны по ссылке которую вы пришлете наставнику.

![Alt text](https://portomebel.ru/upload/loft/15.png)

На гите появится вот такая запись 

![Alt text](https://portomebel.ru/upload/loft/16.png)

### Добавляем настаника в collaborators ###
1. Открываем вкладку Settings
2. Переходим в раздел collaborators
3. Пишем ник настаника 
4. Жмем на кнопку

![Alt text](https://portomebel.ru/upload/loft/17.png)

### Пишем наставнику, что все сделали, ждем ответа. ###

## 4. Доработка

Далее делаем доработки, коммитим их и пушим в туже ветку из которой создавали pull request.(не забываем сделать пуш в gh-pages ветку, чтобы изменения отобразились на gh-pages) 

**Новый pull request создавать не нужно** (вы и не сможете создать новый, пока я не закрыл старый), изменения подтянутся в прошлый. 

**Пишем наставнику, что все поправили, ждем ответа.**

## 5. Новые задания

После того как настаник примет задание вашей первой недели он смержит в мастер все изменения (это делаем именно наставник, т.е. **сами** пулреквест **не закрываем!**). 
Вы проверяете что находитесь на нужно(актуальной) ветке и из нее создаете новую ветку week_2 (или друю недельную ветку)
```{r, engine='bash', count_lines}
git checkout -b week_2
```
Работаете в новой ветке, делаете коммит и пуш на удаленный репозиторий 


Создаете новый pull request и снова пишите настанику

