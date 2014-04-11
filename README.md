# Настроки Ubuntu 13.04 под Ruby on Rails (manual)

#### Выполняем
`sudo apt-get install subl` - качаем Sublima Text 3 (или же собираем руками). Желательно его купить, что бы окошко о покупке не мазолило глаз.
`sudo apt-get install tmux` - качаем менеджер терминала, для отображения нескольких output в одном терминальном окне  
В настройках терминала меняем hot keys на Copy Past (Ctrl-c Ctrl-v)

#### Пути для файлов
`~/.bash_aliases`   
`~/.tmux.conf`  
`/bin/tmux-s`
`/bin/tmux-ss`
`/bin/tmux-st` 
  
#### Настройка Sublima Text 3
Скопировать содержимое **Sublima Text 3 - User Preference** в *Prefersnces -> Settings-User* (меню программы)  
Так же прочитать статью http://vstarkov.ru/sublime-workflow/   
Установка PackageManager: `import urllib.request,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)`  
Поставить Node.js,, Package Control, тему «Soda Theme», Monokai Soda.tmTheme, Sublime Linter, Sublime Linter-ruby, Emmet
  
#### Настройка алиасов:
 *Создать и(или) дописать в .bash_aliases:*  
`alias ls='ls -ApC --color=auto'`  
`alias lsdir='find . -type f -exec ls {} \; 2> /dev/null'`  
`alias update='sudo apt-get update && sudo apt-get -y --force-yes  upgrade'`  
`alias rapp='cd ~/work/ruby/Apps/sample_app'`  
`alias rappo='cd ~/work/ruby/Apps/sample_app && subl .'`  
`alias rapps='/bin/bash --login'`  
`alias rappo='cd ~/work/ruby/Apps/sample_app && subl .'`  
`alias tmux-k='tmux kill-session'`  
`alias tmux-ko='tmux kill-server'`  
`alias tmux-l='tmux ls'`  
`alias rrmm="git status --porcelain | sed -e 's/^[\sA-Z\?]*\s//' | xargs --delim='\n' rm -rfv"` 
 
> После сохраниения *.bash_aliases* для вступления в силу новых алиасов необходимо перезапустить терминал

#### Настройка tmux:
Скопировать файлы *.tmux.conf* и *tmux-s* из данного репозитория в папки, указанные выше.  
Команда (из папки с файлом): `mv .tmux.conf ~/`  `sudo mv tmux-s /bin`
> После копирования выйти из всех текущих сессий *tmux* или прибить сервер и создать новыю сессию  

######Команды tmux:
* `tmux kill-server` or `tmux-ko` - убиваем сервер
* `tmux kill-session` or `tmux-k` - убиваем сервер
* `tmux ls` or `tmux-l` - просматриваем существующие сессии
* `tmux attach` or `tmux a` - подключаемся (аттачимся) к сессии (может принимать имя сессии)
* `tmux new -s _name_` - создаем новую сессию с именем *_name_*
* `tmux-s` - создат новую сессию и настраивает *tmux* для работы с **Ruby on Rails* (подробнее ниже)

######Hot-keys tmux:
* `Ctrl-b` - default hostkey
* `Ctrl-q` - custom hostkey
*
* `hostkey  c` - создать новое окно
* `hostkey  1..9` - переключение между окнами по номерам
* `hostkey p` - previous window
* `hostkey n` - next window
* `hostkey l` - ‘last’ (previously used) window
* `hostkey w` - choose window from a list
* `hostkeya ,` - rename the current window
* `hostkeya &`  - kill the current window
* 
* `hostkey  |`- разделение текущего окна по горизонтали  
* `hostkey  -` - разделение текущего окна по вертикали 
* `hostkey стрелки (одно нажатие)` - перемешение между панелями
* `hostkey стрелки (много нажатий с удержанием hostkey)` - перемешение границ окна
* 
* `hostkey  d` - deattach (отключение от сессии)  

> Практически во всех сокращениях сначало жмем hostkey, затем отпускаем и жмем второй символ

######Hot-keys terminal:
* `Ctrl-Shift-c` - оборвать текущую операцию  
* `Ctrl-Shift-d` - убить или выйти из текущей программы (задачи)  

#### O bash-скрипте *tmux-s*:
После копирования сего файла в папку bin (`sudo mv tmux-s /bin`) Необходимо сделать его исполняемым: `sudo chmod +x tmux-s`. После этих нехитрых танцев наш скрипт превращается в полноценную команду терминала. Разберем скрипт.  

В скрипте вы можете видеть блок *Config Variables*. В этом блоке описаны имя создаваемой сессии и окна при вызоме `tmux-s`  
Скрипт может быть запучен без параметров, ис различными комбинациями четырех параметров:
* `запуск без параметров` создает нову сессию, новое окно и разбивает его на три панели (фокус в первой панели, она больше всех остальных)
* `-s` запускает во второй панели (правая верхняя) Rails сервер
* `-t` запускает в третей панели Guard+Spork (среда TDD RSpec)
* `-o` открывает наш проект (путь задается в алиасе rappo) при старте tmux-s
* `-c` в перваой панели запускается Rails-консоль  

Можно запускать *tmux-s* как с одним так и с несколькими параметрами в любой последовательности. К примеру: `tmux-s -s -t` запустит новую сессию *tmux* а так же Rails-сервер и Guard+Spork

#### Литература и ссылки:
http://brainscraps.wikia.com/wiki/Resurrecting_tmux_Sessions_After_Reboot
