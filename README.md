﻿# Базовый порядок работы с Git (GitHub)

### Открываем терминал в Linux (Windows или MacOS) и работаем по следующему примерному алгоритму:

1. Проверка установки Git на компьютере: __git version__

2. Установка Git через терминал в Linux Mint: __apt-get install git__

3. Указание имени пользователя в настройках Git. Флаг —global позволяет сделать это, находясь в любой директории: __git config --global user.name "User Name"__

4. Указание e-mail в настройках Git. Флаг —global позволяет сделать это, находясь в любой директории: __git config --global user.email username@yandex.ru__

5. Проверка содержимого глобальных настроек Git, хранящихся в файле .gitconfig в домашней директории: __cat ~/.gitconfig__ или __git config —list__

6. Создание репозитория Git в папке проекта (предварительно необходимо перейти в папку проекта, используя команду cd в терминале): __cd <папка с проектом>, git -init__

7. Изменение имени ветки «Master» на «Main»: __git branch -m «main»__

8. Если под контроль версий неправильно выбрана папка, то снять контроль версий с папки можно удалением скрытой подпапки .git: __cd <папка с репозиторием>__, __rm -rf .git__

9. Проверка текущего состояния репозитория: __git status__

10. Добавление конкретного файла или всех файлов папки в репозиторий git: __git add <файл.расширение>__, __git add -all__ или __git add .__

11. Выполнение коммита (флаг -m добавляет сообщение к коммиту): __git commit -m «сообщение об изменениях»__

12. Просмотр истории коммитов: __git log__

13. После создания удаленного репозитория на GitHub, для связки его с локальным репозиторием необходимо проверить наличие SSH ключей (публичного и приватного). Они обычно находятся в корневой папке в скрытой директории .ssh/: __cd ~__, __ls -la .ssh/__

14. Генерация SSH-ключа. Алгоритм 1. Если при вводе команды происходит ошибка, то нужно воспользоваться другми алгоритмом: __ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"__ 

15. Генерация SSH-ключа. Алгоритм 2: __ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"__

16. Проверка наличия новых созданных SSH ключей: __ls -a ~/.ssh__

17. Привязывание SSH-ключа с GitHub аккаунта: __cat ~/.ssh/id_rsa.pub__ или __cat ~/.ssh/id_ed25519.pub__ и копируем SSH-ключ в буфер обмена

18. Переход на GitHub. В аккаунте в «Settings», в пункте «SSH and GPG keys» выбрать «New SSH Keys». В поле «Title» написать «Personal key». В поле «Key» скопируйте ваш ключ из буфера обмена.

19. После чего нажмите «Add SSH key»

20. Проверка правильности SSH ключа: __ssh -T git@github.com__

21. Для привязки удаленного репозитория к локальному необходимо перейти на страницу удаленного репозитория, выбрать тип «SSH» и скопировать URL.

22. Привязка удаленного репозитория к локальному (предварительно необходимо перейти в папку с проектом): __cd <папка с проектом>__ 

23. Откройте консоль, перейдите в каталог локального репозитория и введите команду «git remote add». Команде необходимо передать два параметра: имя удалённого репозитория и его URL. В качестве имени используйте слово «origin», а URL вы скопировали со страницы удалённого репозитория: __git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git__

24. Убедиться, что локальный и удаленный репозитории связаны можно с помощью команды: __git remote — v__

25. Синхронизация локального репозитория с удаленным. Первый раз это делается с флагом -u и параметрами origin (имя удалённого репозитория) и main или master (название текущей ветки). Флаг -u свяжет локальную ветку с одноимённой удалённой: __git push -u origin main или git push -u origin master__

26. Сокращенный лог: __git log --online__


