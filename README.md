# timp-lab02
**Part1**

1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).

2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
```bash
echo "# timp-lab02" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:amandreev17/timp-lab02.git
git push -u origin main
подсказка: Using 'master' as the name for the initial branch. This default branch name
подсказка: is subject to change. To configure the initial branch name to use in all
подсказка: of your new repositories, which will suppress this warning, call:
подсказка: 
подсказка: 	git config --global init.defaultBranch <name>
подсказка: 
подсказка: Names commonly chosen instead of 'master' are 'main', 'trunk' and
подсказка: 'development'. The just-created branch can be renamed via this command:
подсказка: 
подсказка: 	git branch -m <name>
Инициализирован пустой репозиторий Git в /home/artyom-andreev/Рабочий стол/.git/
[master (корневой коммит) 62bedc2] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
Перечисление объектов: 3, готово.
Подсчет объектов: 100% (3/3), готово.
Запись объектов: 100% (3/3), 226 байтов | 28.00 КиБ/с, готово.
Всего 3 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
To github.com:amandreev17/timp-lab02.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```
   
   
3. Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.
```bash
$ touch hello_world.cpp

'''#include <iostream>
using namespace std;

int main() {
    cout << "Hello, world" << endl;
}'''
```
    
4. Добавьте этот файл в локальную копию репозитория.
```bash
$ git add hello_world.cpp
```
   
5. Закоммитьте изменения с осмысленным сообщением.
```bash
$ git commit -m "Added initial version of hello_world.cpp with bad coding style."

[main ce2f047] added fail with bad codestyle
 1 file changed, 7 insertions(+)
 create mode 100644 timp-lab02/hello-world.cpp
```
   
6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.
```bash
'''
#include <iostream>
#include <string>
using namespace std;

int main() {
    string name;
    cin >> name;
    cout << "Hello, world " << name << endl;
}
'''
```
    
7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add? Потому что при использовании опции `-a` ("--ammend") в команде `git commit`, Git автоматически добавляет все измененные файлы в коммит.
   
```bash
$ git commit -a -m "by name"

[main b433290] with name
 1 file changed, 4 insertions(+), 1 deletion(-)
```
  
8. Запуште изменения в удалёный репозиторий.
```bash
$ git push origin main

Перечисление объектов: 9, готово.
Подсчет объектов: 100% (9/9), готово.
При сжатии изменений используется до 4 потоков
Сжатие объектов: 100% (6/6), готово.
Запись объектов: 100% (8/8), 837 байтов | 837.00 КиБ/с, готово.
Всего 8 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
To github.com:amandreev17/timp-lab02.git
   62bedc2..b433290  main -> main
```
   
9. Проверьте, что история коммитов доступна в удалёный репозитории.
   

**Part2**

1. В локальной копии репозитория создайте локальную ветку patch1.
```bash
$ git checkout -b patch1

Переключено на новую ветку «patch1»
```
  
2. Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;
```bash
'''
#include <iostream>
#include <string>

int main() {
    std::string name;
    std::cin >> name;
    std::cout << "Hello, world " << name << std::endl;
}
'''
```
   
3. commit, push локальную ветку в удалённый репозиторий.
```bash
$ git add hello_world.cpp
$ git commit -m 'remove using namespase std'

[patch1 807bf4d] remove using namespase std
 1 file changed, 3 insertions(+), 4 deletions(-)
 
$ git push origin patch1

Перечисление объектов: 7, готово.
Подсчет объектов: 100% (7/7), готово.
При сжатии изменений используется до 4 потоков
Сжатие объектов: 100% (3/3), готово.
Запись объектов: 100% (4/4), 447 байтов | 447.00 КиБ/с, готово.
Всего 4 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: 
remote: Create a pull request for 'patch1' on GitHub by visiting:
remote:      https://github.com/amandreev17/timp-lab02/pull/new/patch1
remote: 
To github.com:amandreev17/timp-lab02.git
 * [new branch]      patch1 -> patch1
```
   
4. Проверьте, что ветка patch1 доступна в удалёный репозитории.
   
5. Создайте pull-request patch1 -> master.

   
6. В локальной копии в ветке patch1 добавьте в исходный код комментарии.
```cpp
#include <iostream>
#include <string>

int main() {
    std::string name;
    std::cin >> name; // enter name
    std::cout << "Hello, world " << name << std::endl; // print name
}
```
   
7. commit, push.
```bash
$ git commit -a -m "added comments"

[patch1 025c741] added comments
 1 file changed, 2 insertions(+), 2 deletions(-)

$ git push origin patch1

Перечисление объектов: 7, готово.
Подсчет объектов: 100% (7/7), готово.
При сжатии изменений используется до 4 потоков
Сжатие объектов: 100% (3/3), готово.
Запись объектов: 100% (4/4), 395 байтов | 395.00 КиБ/с, готово.
Всего 4 (изменений 1), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:amandreev17/timp-lab02.git
   807bf4d..025c741  patch1 -> patch1
```
   
8. Проверьте, что новые изменения есть в созданном на шаге 5 pull-request
   
9. В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.
   
10. Локально выполните pull.
```bash
$ git pull origin main

remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (1/1), 905 байтов | 905.00 КиБ/с, готово.
Из github.com:amandreev17/timp-lab02
 * branch            main       -> FETCH_HEAD
   b433290..e7c7e15  main       -> origin/main
Обновление b433290..e7c7e15
Fast-forward
 timp-lab02/hello-world.cpp | 7 +++----
 1 file changed, 3 insertions(+), 4 deletions(-)
```
   
11. С помощью команды git log просмотрите историю в локальной версии ветки master.
```bash
$ git log

commit e7c7e153d6a5db2a7302555fb600dae8e216787d (HEAD -> main, origin/main)
Merge: b433290 025c741
Author: amandreev17 <144845041+amandreev17@users.noreply.github.com>
Date:   Sun Mar 31 17:40:52 2024 +0300

    Merge pull request #1 from amandreev17/patch1
    
    remove using namespase std

commit 025c74134ae42f24ba379a3d2119558036823f79 (origin/patch1)
Author: amandreev17 <a_m_andreev2005@mail.ru>
Date:   Sun Mar 31 17:38:41 2024 +0300

    added comments

commit 807bf4d2e4b3e3eb25f251f9efea599f4f810fc7
Author: amandreev17 <a_m_andreev2005@mail.ru>
Date:   Sun Mar 31 17:33:15 2024 +0300

    remove using namespase std

commit b4332909fe50ab5360ff023b33836b35ca729269
Author: amandreev17 <a_m_andreev2005@mail.ru>
Date:   Sun Mar 31 17:26:54 2024 +0300

    with name

commit ce2f0478e3718fcd3c58e6b7e731e6e6d6b66dc5
Author: amandreev17 <a_m_andreev2005@mail.ru>
Date:   Sun Mar 31 17:20:33 2024 +0300

    added fail with bad codestyle

commit 62bedc2595e938545c5ab63db573f8d093ed83a1
Author: amandreev17 <a_m_andreev2005@mail.ru>
Date:   Sun Mar 31 17:11:33 2024 +0300

    first commit
```
   
12. Удалите локальную ветку patch1.
```bash
$ git branch -d patch1

Ветка patch1 удалена (была 025c741).
```

**Part3**

1. Создайте новую локальную ветку patch2.
```bash
Команда: git checkout -b patch2

Вывод:Переключились на новую ветку «patch2»
```
    
   2) Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla.
```bash
Команда: clang-format -style=Mozilla -i hello_world.cpp
```
   
   3) commit, push, создайте pull-request patch2 -> master.
```bash
Команда: git add hello_world.cpp

Команда:git commit -m "Updated code style using clang-format"
Вывод:[patch2 ebad822] Updated code style using clang-format
 1 file changed, 10 insertions(+), 10 deletions(-)
```
   
   4) В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
Изменяем через графический интерфейс комментарий на русский язык
   
   5) Убедитесь, что в pull-request появились конфликтны.
Пулл реквест пишет, что merge невозможен, у нас конфликт
   
   6) Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.
   
```bash
$ git pull origin main
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 1), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (4/4), 1.03 КиБ | 1.03 МиБ/с, готово.
Из github.com:amandreev17/timp-lab02
 * branch            main       -> FETCH_HEAD
   e7c7e15..40f78eb  main       -> origin/main
Обновление e7c7e15..40f78eb
Fast-forward
 timp-lab02/hello-world.cpp | 6 +++---
 1 file changed, 3 insertions(+), 3 deletions(-)

$ git switch patch2
Переключено на ветку «patch2»


$ git add .

Команда:git commit -m "Commit message here"
[patch2 eb078ff] new chages
 1 file changed, 1 deletion(-)

 
$ git rebase main
Автослияние timp-lab02/hello-world.cpp
КОНФЛИКТ (содержимое): Конфликт слияния в timp-lab02/hello-world.cpp
error: не удалось применить коммит e73f852… Mozilla codestyle
подсказка: Resolve all conflicts manually, mark them as resolved with
подсказка: "git add/rm <conflicted_files>", then run "git rebase --continue".
подсказка: You can instead skip this commit: run "git rebase --skip".
подсказка: To abort and get back to the state before "git rebase", run "git rebase --abort".
Не удалось применить коммит e73f852... Mozilla codestyle

'''
провожу изменения
#include <iostream>
#include <string>

int
main()
{
<<<<<<< HEAD
    std::string name;
    std::cin >> name;                                  // введите имя
    std::cout << "Hello, world " << name << std::endl; // вывод имя
}
=======
  std::string name;
  std::cin >> name;                                  // enter name
  std::cout << "Hello, world " << name << std::endl; // print name
}
>>>>>>> e73f852 (Mozilla codestyle)
'''

$ git add .

Команда:git rebase --continue
[отделённый HEAD 9313ef9] Mozilla codestyle
 1 file changed, 3 insertions(+), 3 deletions(-)
Успешно перемещён и обновлён refs/heads/patch2.
```

   
7. Сделайте force push в ветку patch2
```bash
$ git push origin patch2 --force

Перечисление объектов: 9, готово.
Подсчет объектов: 100% (9/9), готово.
При сжатии изменений используется до 4 потоков
Сжатие объектов: 100% (4/4), готово.
Запись объектов: 100% (6/6), 597 байтов | 597.00 КиБ/с, готово.
Всего 6 (изменений 1), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:amandreev17/timp-lab02.git
 + e73f852...c8c546e patch2 -> patch2 (forced update)
```
   
8. Убедитель, что в pull-request пропали конфликтны.
   
9. Вмержите pull-request patch2 -> master.
