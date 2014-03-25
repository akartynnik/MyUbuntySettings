# Настроки Ubuntu 13.04 под Ruby (manual)

#### Выполняем
`sudo apt-get install subl` - качаем Sublima Text 3 (или же собираем руками). Желательно его крякнуть, что бы окошко о покупке не мазолило глаз. На ютубе есть видос по кряку.  
`sudo apt-get install tmux` - качаем менеджер терминала, для отображения нескольких output в одном терминальном окне  
В настройках терминала меняем hot keys на Copy Past (Ctrl-c Ctrl-v)

#### Пути для файлов
`~/.bash_aliases`   
`~/.tmux.conf`  
`/bin/tmux-session`  
  
#### Настройка Sublima Text 3
Скопировать содержимое **Sublima Text 3 - User Preference** в *Prefersnces -> Settings-User* (меню программы)
  
#### Настройка алиасов:
 *Создать и(или) дописать в .bash_aliases:*  
`alias ls='ls -ApC --color=auto'`  
`alias lsdir='find . -type f -exec ls {} \; 2> /dev/null'`  
`alias update='sudo apt-get update && sudo apt-get -y --force-yes  upgrade'`  
`alias rapp='cd ~/work/ruby/Apps/sample_app'`  
`alias rappo='cd ~/work/ruby/Apps/sample_app && subl .'`  
`alias rapps='/bin/bash --login'`  
`alias rappo='cd ~/work/ruby/Apps/sample_app && subl .'`   
 
> После сохраниения *.bash_aliases* для вступления в силу новых алиасов необходимо перезапустить терминал

#### Настройка tmux:
Скопировать файл *.tmux.conf* из данного репозитория в папку, указанную выше.  
Команда (из папки с файлом): `mv .tmux.conf ~/`  
> После копирования выйти из всех текущих сессий *tmux* или прибить сервер и создать новыю сессию  

######Команды tmux:
* `tmux kill-server` - убиваем сервер
* `tmux ls` - просматриваем существующие сессии
* `tmux attach` - подключаемся (аттачимся) к сессии (может принимать имя сессии)
* `tmux new -s _name_` - создаем новую сессию с именем *_name_*

######Hot-keys tmux:
* `Ctrl-b` - default hostkey  
* `Ctrl-q` - custom hostkey  
* `hostkey  d` - deattach (отключение от сессии)  
* `hostkey  |`- разделение текущего окна по горизонтали  
* `hostkey  -` - разделение текущего окна по вертикали  
* `hostkey стрелки (одно нажатие)` - перемешение между окнами  
* `hostkey стрелки (много нажатий с удержанием hostkey)` - перемешение границ окна

> Практически во всех сокращениях сначало жмем hostkey, затем отпускаем и жмем второй символ

######Hot-keys terminal:
* `Ctrl-Shift-c` - оборвать текущую операцию  
* `Ctrl-Shift-d` - убить или выйти из текущей программы (задачи)
  
