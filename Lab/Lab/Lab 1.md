# **Лабораторная работа**

1. Изучите разделы man bash, почитайте о настройках самого bash:
   какой переменной можно задать длину журнала history, и на какой строчке manual это описывается?
   HISTSIZE и HISTFILESIZE. Первая отвечает за кол-во строк журнала во время сессии, вторая за то, сколько сохранится по окончанию и запуску сессии строк. 1194 строка. 
   что делает директива ignoreboth в bash?
   Не записывает в журнал повторяющиеся команды или те, что с пробела начинаются. 

2. В каких сценариях использования применимы скобки {}, на какой строчке man bash это описано?
   Группировка команд. 343 строка: 
          { list; }
                 list  is simply executed in the current shell environment.  list
                 must be terminated with a newline or semicolon.  This  is  known
                 as  a  group  command.   The return status is the exit status of
                 list.  Note that unlike the metacharacters ( and ), { and }  are
                 reserved words and must occur where a reserved word is permitted
                 to be recognized.  Since they do not cause a  word  break,  they
                 must  be  separated  from  list  by  whitespace or another shell
                 metacharacter.
3. С учётом ответа на предыдущий вопрос подумайте, как создать однократным вызовом touch 100 000 файлов. Получится ли аналогичным образом создать 300 000 файлов? Если нет, то объясните, почему.
   touch {1..100 000}
   Слишком длинный лист.
![Screenshot_127](https://github.com/user-attachments/assets/5037b050-3ba9-4f88-a36e-9cbd2fb5b39d)

5. В man bash поищите по /\[\[. Что делает конструкция [[ -d /tmp ]]?
   Проверяет наличие папки /tmp. И возвращает ноль. 
6. Сделайте так, чтобы в выводе команды type -a bash первым стояла запись с нестандартным путём, например, bash is... Используйте знания о просмотре существующих и создании новых переменных окружения, обратите внимание на переменную окружения PATH.

    bash is /tmp/new_path_directory/bash
bash is /usr/local/bin/bash
bash is /bin/bash
Другие строки могут отличаться содержимым и порядком. В качестве ответа приведите команды, которые позволили вам добиться указанного вывода, или соответствующие скриншоты.
Ответ: через echo и export прописать еще одну часть к пути.
![Screenshot_129](https://github.com/user-attachments/assets/e8f7fcaa-aef6-42da-9b5e-d6eeb4f54247)

И она туда записывается! Но даже при комбинации все равно не выдает так. 
Задать новый путь через переменную – вышло. теперь там есть /some/new/path. Но как связать type и export. Через function может быть. 
![Screenshot_130](https://github.com/user-attachments/assets/5ff0af53-0618-4156-9054-93cc72b4f9c7)

6. Чем отличается планирование команд с помощью batch и at?
   at – исполнение команды в заданное время
   batch – когда загрузка системы позволяет запустить задание (менее загружена)

