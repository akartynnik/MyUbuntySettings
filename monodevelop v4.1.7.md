Installing MonoDevelop v4.1.7

First install `mono-3-opt-gtk-sharp` package  
Then go to `http://mono-d.alexanderbothe.com/download/`

Возможные ошибки в новой версии - пе правильно читаются файлы *.designer.cs.* 
Проблема кроется в том, что старые версии monodevelop неверно записывали файлы 
*.resource*. Мне помогло пересохранение всех *.designer.cs.* самой monodevelop
либо удаление всех *.resource* файлов.
