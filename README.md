# Домашнее задание к занятию «Основы Git»

### Цель задания

В результате выполнения задания вы:

* научитесь работать с Git, как с распределённой системой контроля версий; 
* сможете создавать и настраивать репозиторий для работы в GitHub, GitLab и Bitbucket; 
* попрактикуетесь работать с тегами;
* поработаете с Git при помощи визуального редактора.

### Чеклист готовности к домашнему заданию

1. Установлена консольная утилита для работы с Git.
2. Есть возможность зарегистрироваться на GitHub, GitLab.
3. Регистрация на Bitbucket не является обязательной. 


### Инструкция к заданию

1. В личном кабинете отправьте на проверку ссылки на ваши репозитории.
2. Любые вопросы по решению задач задавайте в чате учебной группы.

------

## Задание 1. Знакомимся с GitLab и Bitbucket 

Из-за сложности доступа к Bitbucket в работе достаточно использовать два репозитория: GitHub и GitLab.

Иногда при работе с Git-репозиториями надо настроить свой локальный репозиторий так, чтобы можно было 
отправлять и принимать изменения из нескольких удалённых репозиториев. 

Это может понадобиться при работе над проектом с открытым исходным кодом, если автор проекта не даёт права на запись в основной репозиторий.

Также некоторые распределённые команды используют такой принцип работы, когда каждый разработчик имеет свой репозиторий, а в основной репозиторий пушатся только конечные результаты 
работы над задачами. 

### GitLab

Создадим аккаунт в GitLab, если у вас его ещё нет:

1. GitLab. Для [регистрации](https://gitlab.com/users/sign_up)  можно использовать аккаунт Google, GitHub и другие. 
1. После регистрации или авторизации в GitLab создайте новый проект, нажав на ссылку `Create a projet`. 
Желательно назвать также, как и в GitHub — `devops-netology` и `visibility level`, выбрать `Public`.
1. Галочку `Initialize repository with a README` лучше не ставить, чтобы не пришлось разрешать конфликты.
1. Если вы зарегистрировались при помощи аккаунта в другой системе и не указали пароль, то увидите сообщение:
`You won't be able to pull or push project code via HTTPS until you set a password on your account`. 
Тогда перейдите [по ссылке](https://gitlab.com/profile/password/edit) из этого сообщения и задайте пароль. 
Если вы уже умеете пользоваться SSH-ключами, то воспользуйтесь этой возможностью (подробнее про SSH мы поговорим в следующем учебном блоке).
1. Перейдите на страницу созданного вами репозитория, URL будет примерно такой:
https://gitlab.com/YOUR_LOGIN/devops-netology. Изучите предлагаемые варианты для начала работы в репозитории в секции
`Command line instructions`. 
1. Запомните вывод команды `git remote -v`.
1. Из-за того, что это будет наш дополнительный репозиторий, ни один вариант из перечисленных в инструкции (на странице 
вновь созданного репозитория) нам не подходит. Поэтому добавляем этот репозиторий, как дополнительный `remote`, к созданному
репозиторию в рамках предыдущего домашнего задания:
`git remote add gitlab https://gitlab.com/YOUR_LOGIN/devops-netology.git`.
1. Отправьте изменения в новый удалённый репозиторий `git push -u gitlab main`.
1. Обратите внимание, как изменился результат работы команды `git remote -v`.

#### Как изменить видимость репозитория в  GitLab — сделать его публичным 

* На верхней панели выберите «Меню» -> «Проекты» и найдите свой проект.
* На левой боковой панели выберите «Настройки» -> «Основные».
* Разверните раздел «Видимость» -> «Функции проекта» -> «Разрешения».
* Измените видимость проекта на Public.
* Нажмите «Сохранить изменения».

### Bitbucket* (задание со звёздочкой) 

Это самостоятельное задание, его выполнение необязательно.
____

Теперь необходимо проделать всё то же самое с [Bitbucket](https://bitbucket.org/). 

1. Обратите внимание, что репозиторий должен быть публичным — отключите галочку `private repository` при создании репозитория.
2. На вопрос `Include a README?` отвечайте отказом.
3. В отличии от GitHub и GitLab в Bitbucket репозиторий должен принадлежать проекту, поэтому во время создания репозитория 
надо создать и проект, который можно назвать, например, `netology`.
4. Аналогично GitLab на странице вновь созданного проекта выберите `https`, чтобы получить ссылку, и добавьте этот репозиторий, как 
`git remote add bitbucket ...`.
5. Обратите внимание, как изменился результат работы команды `git remote -v`.

Если всё проделано правильно, то результат команды `git remote -v` должен быть следующий:

```bash
$ git remote -v
bitbucket https://andreyborue@bitbucket.org/andreyborue/devops-netology.git (fetch)
bitbucket https://andreyborue@bitbucket.org/andreyborue/devops-netology.git (push)
gitlab	  https://gitlab.com/andrey.borue/devops-netology.git (fetch)
gitlab	  https://gitlab.com/andrey.borue/devops-netology.git (push)
origin	  https://github.com/andrey-borue/devops-netology.git (fetch)
origin	  https://github.com/andrey-borue/devops-netology.git (push)
```

Дополнительно можете добавить удалённые репозитории по `ssh`, тогда результат будет примерно такой:

```bash
git remote -v
bitbucket	git@bitbucket.org:andreyborue/devops-netology.git (fetch)
bitbucket	git@bitbucket.org:andreyborue/devops-netology.git (push)
bitbucket-https	https://andreyborue@bitbucket.org/andreyborue/devops-netology.git (fetch)
bitbucket-https	https://andreyborue@bitbucket.org/andreyborue/devops-netology.git (push)
gitlab	git@gitlab.com:andrey.borue/devops-netology.git (fetch)
gitlab	git@gitlab.com:andrey.borue/devops-netology.git (push)
gitlab-https	https://gitlab.com/andrey.borue/devops-netology.git (fetch)
gitlab-https	https://gitlab.com/andrey.borue/devops-netology.git (push)
origin	git@github.com:andrey-borue/devops-netology.git (fetch)
origin	git@github.com:andrey-borue/devops-netology.git (push)
origin-https	https://github.com/andrey-borue/devops-netology.git (fetch)
origin-https	https://github.com/andrey-borue/devops-netology.git (push)
```

Выполните push локальной ветки `main` в новые репозитории. 

Подсказка: `git push -u gitlab main`. На этом этапе история коммитов во всех трёх репозиториях должна совпадать. 

## РЕШЕНИЕ 1. Знакомимся с GitLab и Bitbucket

Последовательность действий в скриншотах:

**GITLAB**

[repo](https://github.com/sash3939/-Git/assets/156709540/5a766f4e-cafe-4548-a136-b2b87640d07c)
----

[git remote -v](https://github.com/sash3939/-Git/assets/156709540/d527b608-d7a9-4073-98a5-47b1f33ecf01)
----

[git push](https://github.com/sash3939/-Git/assets/156709540/c4111a57-d820-42ea-9039-45fa66f4fd6f)
----

[git remote after push https](https://github.com/sash3939/-Git/assets/156709540/a3f10969-2707-4404-ac7c-21d90f7fea2f)
----

[web gitlab](https://github.com/sash3939/-Git/assets/156709540/ddcbdefa-eee6-4adb-a773-1278712ff3f1)
----

**BITBUCKET**

[create repo](https://github.com/sash3939/-Git/assets/156709540/0976f925-d31f-4732-919b-0da5e66052fa)
----

[git remote -v](https://github.com/sash3939/-Git/assets/156709540/486ed2c3-a4b3-47a0-a147-b4d794204a78)
----

[git push ssh](https://github.com/sash3939/-Git/assets/156709540/4bd1ff3e-1742-47e9-8e96-27d8c4669cf6)
----

[git push bitbucket](https://github.com/sash3939/-Git/assets/156709540/77c4a9b3-059f-436d-85bf-7788e701dc22)
----

[web bitbucket](https://github.com/sash3939/-Git/assets/156709540/1b691883-e68d-4023-93e3-931b86acb890)
----

----


## Задание 2. Теги

Представьте ситуацию, когда в коде была обнаружена ошибка — надо вернуться на предыдущую версию кода,
исправить её и выложить исправленный код в продакшн. Мы никуда не будем выкладывать код, но пометим некоторые коммиты тегами и создадим от них ветки. 

1. Создайте легковестный тег `v0.0` на HEAD-коммите и запуште его во все три добавленных на предыдущем этапе `upstream`.
2. Аналогично создайте аннотированный тег `v0.1`.
3. Перейдите на страницу просмотра тегов в GitHab (и в других репозиториях) и посмотрите, чем отличаются созданные теги. 
    * в GitHub — https://github.com/YOUR_ACCOUNT/devops-netology/releases;
    * в GitLab — https://gitlab.com/YOUR_ACCOUNT/devops-netology/-/tags;
    * в Bitbucket — список тегов расположен в выпадающем меню веток на отдельной вкладке. 

## РЕШЕНИЕ 2. Теги


[create ann tag](https://github.com/sash3939/-Git/assets/156709540/5ed1a03f-79b4-4179-a890-ced5d4fadb0e)
----

[git push](https://github.com/sash3939/-Git/assets/156709540/925a8fbe-bcc5-423d-83bb-90657bccf761)
----

[git push1](https://github.com/sash3939/-Git/assets/156709540/6b8beac2-ca13-4b0f-a495-f398252d214a)
----

----

[git push v0.1](https://github.com/sash3939/-Git/assets/156709540/123380dc-9304-43ac-888d-5318e939f2a6)
----

[tags cmd](https://github.com/sash3939/-Git/assets/156709540/7c323779-69ba-4656-aa70-25aeb8246a7f)
----

[github tags](https://github.com/sash3939/-Git/assets/156709540/c6fd530b-1cb9-4f34-a181-8f4def3cea66)
----

[bitbucket tags](https://github.com/sash3939/-Git/assets/156709540/5b58ccf5-a098-4618-a656-d9c7c06cdb9f)
----

[gitlab tags](https://github.com/sash3939/-Git/assets/156709540/fefc84d2-31d6-41ff-8bfc-8a0567eab8dc)
----



----




## Задание 3. Ветки 

Давайте посмотрим, как будет выглядеть история коммитов при создании веток. 

1. Переключитесь обратно на ветку `main`, которая должна быть связана с веткой `main` репозитория на `github`.
2. Посмотрите лог коммитов и найдите хеш коммита с названием `Prepare to delete and move`, который был создан в пределах предыдущего домашнего задания.
3. Выполните `git checkout` по хешу найденного коммита.
4. Создайте новую ветку `fix`, базируясь на этом коммите `git switch -c fix`.
5. Отправьте новую ветку в репозиторий на GitHub `git push -u origin fix`.
6. Посмотрите, как визуально выглядит ваша схема коммитов: https://github.com/YOUR_ACCOUNT/devops-netology/network.
7. Теперь измените содержание файла `README.md`, добавив новую строчку.
8. Отправьте изменения в репозиторий и посмотрите, как изменится схема на странице https://github.com/YOUR_ACCOUNT/devops-netology/network 
и как изменится вывод команды `git log`.


## РЕШЕНИЕ 3. Ветки

1. [main](https://github.com/sash3939/-Git/assets/156709540/8fdf9cfb-ceab-4f48-9fb5-8d7f155ce61b)
   ----

2. [git log --grep](https://github.com/sash3939/-Git/assets/156709540/13b152cd-601c-4500-873b-8e9b3e940ba4)
   ----

3. [git checkout commit](https://github.com/sash3939/-Git/assets/156709540/7b5c27ca-6430-4ff8-a5cf-f19454b0fcd7)
   ----

4. [branch fix](https://github.com/sash3939/-Git/assets/156709540/c7ed0b00-67b0-4688-a918-b12c67fcdd41)
   ----

5. [git push](https://github.com/sash3939/-Git/assets/156709540/c8dfc5d1-2cfb-483f-9885-2101be68b8d8)
   ----

6. [network](https://github.com/sash3939/-Git/assets/156709540/82b43021-168e-4f1c-a64e-4d2a37684bd4)
   ----

7,8. [change](https://github.com/sash3939/-Git/assets/156709540/e91100a5-4bd9-4c8c-8aa9-416c5f5729fc)
     [git log](https://github.com/sash3939/-Git/assets/156709540/ff85cf33-715b-49fd-8727-dc107e2f9566)
      
    ----


## Задание 4. Упрощаем себе жизнь

Попробуем поработь с Git при помощи визуального редактора. 

1. В используемой IDE PyCharm откройте визуальный редактор работы с Git, находящийся в меню View -> Tool Windows -> Git.
2. Измените какой-нибудь файл, и он сразу появится на вкладке `Local Changes`, отсюда можно выполнить коммит, нажав на кнопку внизу этого диалога.
3. Элементы управления для работы с Git будут выглядеть примерно так:

   ![Работа с гитом](img/ide-git-01.jpg)

4. Попробуйте выполнить пару коммитов, используя IDE. 

[По ссылке](https://www.jetbrains.com/help/pycharm/commit-and-push-changes.html) можно найти справочную информацию по визуальному интерфейсу. 

Если вверху экрана выбрать свою операционную систему, можно посмотреть горячие клавиши для работы с Git. 
Подробней о визуальном интерфейсе мы расскажем на одной из следующих лекций.

*В качестве результата работы по всем заданиям приложите ссылки на ваши репозитории в GitHub, GitLab и Bitbucket*.  
 
## РЕШЕНИЕ 4. Упрощаем себе жизнь

[change README](https://github.com/sash3939/-Git/assets/156709540/94a89637-1ea9-48c4-9d4a-79625d28de2d)
----

[view changes](https://github.com/sash3939/-Git/assets/156709540/132777ac-2ec6-4b0e-aff6-be6acffe8003)
----

[push](https://github.com/sash3939/-Git/assets/156709540/94f0043e-fd96-4ab0-899e-fa5230a228ce)
----

[github changes](https://github.com/sash3939/-Git/assets/156709540/66775437-6fe8-43dc-ae50-6e6c996b9713)
----




https://github.com/sash-39/devops-netology/tree/main
----

https://bitbucket.org/sash_39/devops-netology/src/main/
----

https://gitlab.com/sash-39/devops-netology
----


----
