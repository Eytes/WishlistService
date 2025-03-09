# WishlistService

# Работа с подподулями git

## Добавить репозиторий как подмодуль (Git Submodule)
Если нужно подтянуть код другого репозитория внутрь текущего проекта:

```shell
git submodule add https://github.com/username/repository-name.git path/to/submodule
```

После этого в проекте появится папка path/to/submodule, связанная с внешним репозиторием.
Чтобы обновить подмодуль:
```shell
git submodule update --remote --merge
```
## Если нужно удалить подмодуль в Git, сделай следующее:

1. Удаление записи о подмодуле в `.gitmodules`. Открой файл `.gitmodules` и удали секцию, связанную с подмодулем.

    Или выполни команду:
    ```shell
    git config --remove-section submodule.path/to/submodule
    ```

2. Удаление записи из `.git/config`. Записи о подмодуле хранятся в `.git/config`. Удали их вручную или используй:

    ```shell
    git config --remove-section submodule.path/to/submodule
    ```

3. Удаление записей из `.git/modules`. 

    ```shell
    rm -rf .git/modules/path/to/submodule
    ```
4. Удаление папки подмодуля и коммит изменений

    ```shell
    git rm -rf path/to/submodule
    git commit -m "Удалён подмодуль path/to/submodule"
    ```

5. Обновление репозитория
    ```shell
    git gc --prune=now
    git push origin main  # (или другая ветка)
    ```
