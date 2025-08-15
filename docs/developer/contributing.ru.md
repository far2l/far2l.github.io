# Руководство для контрибьюторов

Этот раздел предназначен для тех, кто хочет внести свой вклад в код far2l.

### Полезные ресурсы

*   **Описание API и отличий от Windows:** [HACKING.md](https://github.com/elfmz/far2l/blob/master/HACKING.md)
*   **Стиль кода:** [CODESTYLE.md](https://github.com/elfmz/far2l/blob/master/CODESTYLE.md) (кратко: `CamelCase` для функций, `snake_case` для переменных в новом коде).
*   **Энциклопедия FAR 2:** Незаменимый ресурс по языку макросов и формату файлов помощи ([ссылка на CHM](https://github.com/elfmz/far2l/issues/1135)).

### Отладка

#### Отладочные логи (printf-style)

Самый простой способ отследить выполнение кода — добавить вывод в `stderr`.

1.  **Включите вывод логов**, запустив far2l с переменной окружения:
    ```shell
    # Вывод в консоль
    export FAR2L_STD=-
    far2l

    # Вывод в файл
    export FAR2L_STD=/path/to/log.txt
    far2l
    ```
2.  **Добавьте вывод в коде:**
    ```cpp
    #include <stdio.h>

    // ...
    fprintf(stderr, "My debug message: value = %d\n", my_variable);
    ```

**Шпаргалка по выводу разных типов строк:**
```cpp
FARString sample;
fprintf(stderr, "%ls\n", sample.CPtr()); // как wchar_t*
fprintf(stderr, "%s\n", sample.GetMB().c_str()); // как char*

std::wstring w_sample;
fprintf(stderr, "%ls\n", w_sample.c_str());

std::string s_sample;
fprintf(stderr, "%s\n", s_sample.c_str());
```

#### Использование GDB

При падении или зависании программы, информация из GDB бесценна.

1.  Запустите far2l под отладчиком: `gdb far2l`
2.  Внутри GDB введите `run`.
3.  Воспроизведите проблему (падение или зависание).
4.  **Если программа упала**, GDB остановится сам. Введите `bt` (backtrace) и скопируйте вывод.
5.  **Если программа зависла**, переключитесь в терминал с GDB, нажмите `Ctrl+C`, а затем введите `thread apply all bt` и скопируйте вывод.

### Локализация (добавление строк и справки)

*   **Языковые строки:**
    *   Все строки интерфейса находятся в файле `far2l/bootstrap/scripts/farlang.templ.m4`.
    *   При добавлении новой строки **обязательно** добавьте ее для всех 9 языков.
    *   Если перевод для какого-то языка неизвестен, используйте префикс `upd:`, например: `upd:"English stub"`.
*   **Файлы помощи:**
    *   Исходники лежат в `far2l/bootstrap/scripts/*.hlf.m4`.