1."Работа с историей изминений"----------------------------------------------------------

        1.1.  
        git log develop-feature1 --since=3.hours --not master develop
      
        Вывод лога за последние 3 часа с коммитами которые находятся в develop-feature1 ветке и только в ней. 

        1.2   
        git log master develop --grep='231' --pretty=format:"%Cgreen%s:  %Cred%an  %Cblue%ad"     
        
        Указывем в команде git log имена веток(master, branch). Далее, с помощью опции grep ставим паттерн для поиска в сообщении коммита(231) и в конце выставляем паттерн для понятного оутпута.


-----------------------------------------------------------------------------------------

2."Избирательное слияние"----------------------------------------------------------------

        2.1  
        a) git log develop-feature1 --online
        Выведем в одну строку хеш коммита и его сообщение.
        Запомним хеш коммита, который мы хотим включить в develop.
     
        б) git checkout develop
        Перейдем в develop ветку.

        в) git cherry-pick <хеш выбранного коммита>
        С помощью команды git cherry-pick включим выбранный нами коммит в ветку develop.

-----------------------------------------------------------------------------------------

3."Исправление ошибок"-------------------------------------------------------------------     
       
       a)git checkout develop-feature3
       Перейдем в ветку.
       
       б)git rebase -i HEAD~3
       Возьмем последние 3 коммита для примера.

       в)Далeе в интерактивном меню выберем команду reword.
       pick f7f3f6d 1 commit
       pick 310154e 2 commit
       pick a5f4a0d 3 commit

       # Rebase 710f0f8..a5f4a0d onto 710f0f8
       #
       # Commands:
       #  p, pick = use commit
       #  r, reword = use commit, but edit the commit message
       #  e, edit = use commit, but stop for amending
       #  s, squash = use commit, but meld into previous commit
       #  f, fixup = like "squash", but discard this commit's log message
       #  x, exec = run command (the rest of the line) using shell
       #
       # These lines can be re-ordered; they are executed from top to bottom.
       #
       # If you remove a line here THAT COMMIT WILL BE LOST.
       #
       # However, if you remove everything, the rebase will be aborted.
       #
       # Note that empty commits are commented out

       г)
       <тут должно быть сообщение коммита> - изменяйте его 

       # Please enter the commit message for your changes. Lines starting
       # with '#' will be ignored, and an empty message aborts the commit.
       #
       # Date:      Wed Jul 6 00:47:07 2016 +0300
       #
       # interactive rebase in progress; onto b4064ec
       # Last commands done (6 commands done):
       #    pick 966183a merged
       #    r a15b9d7 unmerged
       # No commands remaining.
       # You are currently editing a commit while rebasing branch 'develop' on 'b4064ec'.
       #
       # Changes to be committed:
       #       new file:   unmerged
       #

       д) Если у вас один коммит можно воспользоваться коммандой git --amend



       Но на самом деле, эти способы подходят для правки личного удаленного репозитория.
       Крайне нежелательно использовать их, если вы работаете в команде над большим проектом, потому что они переписывают историю коммитов.
       Постарайтесь уладить эту ситуацию с тим лидом на словах.
------------------------------------------------------------------------------------------------------
