# Макросы: автоматизация рутины

Макросы позволяют записывать последовательности действий и назначать их на горячие клавиши.

### Различия: far2l и far2m

*   **far2l** использует классический макроязык из FAR Manager 2. Макросы хранятся в файле `~/.config/far2l/settings/key_macros.ini`.
*   **far2m** использует современный и более мощный язык **Lua**, как в FAR Manager 3. Макросы хранятся в виде `.lua` файлов в каталоге `~/.config/far2m/Macros/scripts/`. Классические макросы в far2m не работают.

### Запись макроса (для far2l)

1.  Нажмите `Ctrl+.` (точка). В углу экрана появится буква `R`, сигнализируя о начале записи.
2.  Выполните последовательность действий, которую хотите автоматизировать.
3.  Снова нажмите `Ctrl+.`.
4.  Нажмите комбинацию клавиш, на которую хотите "повесить" этот макрос.

### Примеры полезных макросов (для far2l)

Добавьте этот код в файл `~/.config/far2l/settings/key_macros.ini`, чтобы упростить себе жизнь.

#### Навигация в стиле Midnight Commander (`Ctrl+S`)

Этот макрос запускает быстрый поиск по `Ctrl+S`, как в MC.
```ini
[KeyMacros/Shell/CtrlS]
DisableOutput=0x1
Sequence=Alt0 BS
```

#### Макросы для урезанных клавиатур (ноутбуки, macOS)

Если на вашей клавиатуре нет клавиш Ins или цифрового блока.
```ini
; Использовать Пробел как Ins на панелях
[KeyMacros/Shell/Space]
DisableOutput=0x1
EmptyCommandLine=0x1
Sequence=Num0

; Имитация Grey+, Grey- и Grey*
[KeyMacros/Shell/Ctrl=]
Sequence=Add
[KeyMacros/Shell/Ctrl-]
Sequence=Subtract
[KeyMacros/Shell/CtrlShift8]
Sequence=Multiply
```

#### Перевод раскладки (XLat) для выделенного текста

```ini
[KeyMacros/Common/CtrlShiftX]
DisableOutput=0x1
Sequence=$If (Selected) $XLat $Else CtrlShiftLeft $XLat CtrlRight $End
Description=XLat selected text or last word
```