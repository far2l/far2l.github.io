# Установка far2l

Существует несколько способов установки far2l. Выберите наиболее удобный для вашей системы.

### Рекомендуемые способы для дистрибутивов

#### Ubuntu, Linux Mint и их производные (через PPA)

Это лучший способ получать самые свежие обновления.

1.  **Подключите PPA репозиторий:**
    ```shell
    sudo add-apt-repository ppa:far2l-team/ppa
    sudo apt update
    ```
2.  **Установите нужную версию:**
    *   Для **GUI-версии** (графический режим, рекомендуется для десктопа):
        ```shell
        sudo apt install far2l-gui
        ```
    *   Для **TTY-версии** (терминальный режим с расширенной поддержкой клавиатуры):
        ```shell
        sudo apt install far2l-ttyx
        ```

#### Fedora, CentOS (через COPR)
```shell
sudo dnf copr enable polter/far2l
sudo dnf install far2l
```

### Portable и AppImage (для любого Linux)

Эти версии не требуют установки и идеально подходят для тестирования или использования на системах без прав администратора.

*   **Скачать:** [**GitHub Releases (spvkgn/far2l-portable)**](https://github.com/spvkgn/far2l-portable/releases)
*   **Использование:**
    1.  Скачайте файл, соответствующий архитектуре вашего процессора (например, `...x86_64.run`).
    2.  Сделайте его исполняемым: `chmod +x far2l_*.run`
    3.  Запустите: `./far2l_*.run`

### Установка из официальных репозиториев

Версия в официальных репозиториях может быть не самой новой, но является стабильной.

*   **Debian / Ubuntu:**
    ```shell
    # Для GUI и TTY версии
    sudo apt install far2l-wx

    # Только для TTY версии
    sudo apt install far2l
    ```

### macOS

Установка через [Homebrew](https://brew.sh/) является самым простым способом:
```shell
brew install --cask far2l
```

### Сборка из исходного кода

Если вам нужна максимальная гибкость, вы можете собрать far2l самостоятельно.

1.  **Установите зависимости** (пример для Debian/Ubuntu):
    ```shell
    sudo apt-get install libwxgtk3.2-dev libx11-dev libxi-dev libxml2-dev libuchardet-dev libssh-dev libssl-dev libsmbclient-dev libnfs-dev libneon27-dev cmake pkg-config g++ git
    ```
2.  **Склонируйте репозиторий и соберите проект:**
    ```shell
    git clone https://github.com/elfmz/far2l
    cd far2l
    mkdir -p _build && cd _build
    cmake -DUSEWX=yes -DCMAKE_BUILD_TYPE=Release ..
    make -j$(nproc)
    ```
3.  **Запустите или установите:**
    *   Запустить: `./install/far2l`
    *   Установить в систему: `sudo make install`