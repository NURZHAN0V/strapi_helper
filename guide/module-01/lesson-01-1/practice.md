# Практические задания: Подготовка среды разработки

## Установка Node.js и npm

### Шаг 1: Скачивание Node.js

1. Перейдите на официальный сайт Node.js: https://nodejs.org/
2. Скачайте LTS версию (рекомендуется)
3. Запустите установщик от имени администратора

### Шаг 2: Установка Node.js

1. Следуйте инструкциям установщика
2. Убедитесь, что опция "Add to PATH" включена
3. Завершите установку

### Шаг 3: Проверка установки

Откройте командную строку и выполните:

```bash
# Проверка версии Node.js
node --version

# Проверка версии npm
npm --version
```

**Ожидаемый результат:**
```
v18.17.0
9.6.7
```

### Шаг 4: Обновление npm (опционально)

```bash
# Обновление npm до последней версии
npm install -g npm@latest
```

## Настройка VS Code

### Шаг 1: Установка VS Code

1. Скачайте VS Code с официального сайта: https://code.visualstudio.com/
2. Установите редактор
3. Запустите VS Code

### Шаг 2: Установка расширений

Откройте VS Code и установите следующие расширения:

1. **ES7+ React/Redux/React-Native snippets**
   - Нажмите `Ctrl+Shift+X`
   - Найдите "ES7+ React/Redux/React-Native snippets"
   - Нажмите "Install"

2. **Prettier - Code formatter**
   - Найдите "Prettier - Code formatter"
   - Установите

3. **ESLint**
   - Найдите "ESLint"
   - Установите

4. **GitLens**
   - Найдите "GitLens"
   - Установите

5. **Material Icon Theme**
   - Найдите "Material Icon Theme"
   - Установите

### Шаг 3: Настройка VS Code

Создайте файл настроек VS Code:

1. Нажмите `Ctrl+Shift+P`
2. Введите "Preferences: Open Settings (JSON)"
3. Добавьте следующие настройки:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  "files.autoSave": "onFocusChange",
  "git.enableSmartCommit": true,
  "git.confirmSync": false
}
```

## Настройка Git

### Шаг 1: Установка Git

1. Скачайте Git с официального сайта: https://git-scm.com/
2. Установите Git с настройками по умолчанию
3. Перезапустите командную строку

### Шаг 2: Настройка Git

Выполните следующие команды:

```bash
# Настройка имени пользователя
git config --global user.name "Ваше Имя"

# Настройка email
git config --global user.email "ваш.email@example.com"

# Настройка редактора по умолчанию
git config --global core.editor "code --wait"

# Настройка основной ветки
git config --global init.defaultBranch main
```

### Шаг 3: Проверка настроек

```bash
# Проверка всех настроек
git config --list

# Проверка версии Git
git --version
```

### Шаг 4: Создание SSH ключа (опционально)

```bash
# Генерация SSH ключа
ssh-keygen -t ed25519 -C "ваш.email@example.com"

# Запуск ssh-agent
eval "$(ssh-agent -s)"

# Добавление ключа в ssh-agent
ssh-add ~/.ssh/id_ed25519

# Копирование публичного ключа (для Windows)
clip < ~/.ssh/id_ed25519.pub
```

## Проверка готовности системы

### Шаг 1: Создание тестового проекта

```bash
# Создание папки для проектов
mkdir strapi-projects
cd strapi-projects

# Создание тестового проекта
mkdir test-project
cd test-project

# Инициализация Git репозитория
git init

# Создание тестового файла
echo "# Test Project" > README.md

# Добавление файла в Git
git add README.md
git commit -m "Initial commit"
```

### Шаг 2: Проверка портов

```bash
# Проверка доступности порта 1337
netstat -an | findstr :1337

# Проверка доступности порта 3000
netstat -an | findstr :3000
```

### Шаг 3: Тестирование npm

```bash
# Создание package.json
npm init -y

# Установка тестового пакета
npm install lodash

# Проверка установки
node -e "console.log(require('lodash').version)"
```

### Шаг 4: Тестирование VS Code

1. Откройте папку проекта в VS Code:
   ```bash
   code .
   ```

2. Создайте тестовый файл `test.js`:
   ```javascript
   console.log('Hello, Strapi!');
   ```

3. Проверьте форматирование кода (Shift+Alt+F)

## Устранение проблем

### Проблема: Node.js не найден в PATH

**Решение:**
1. Перезапустите командную строку
2. Проверьте переменную PATH: `echo $env:PATH`
3. При необходимости добавьте путь к Node.js в PATH

### Проблема: npm команды не работают

**Решение:**
```bash
# Очистка кэша npm
npm cache clean --force

# Переустановка npm
npm install -g npm@latest
```

### Проблема: Git не настроен

**Решение:**
```bash
# Проверка настроек Git
git config --list

# При необходимости настройте имя и email
git config --global user.name "Ваше Имя"
git config --global user.email "ваш.email@example.com"
```

### Проблема: VS Code не открывается из командной строки

**Решение:**
1. Откройте VS Code
2. Нажмите `Ctrl+Shift+P`
3. Введите "Shell Command: Install 'code' command in PATH"
4. Выполните команду

## Проверочный список

Перед переходом к следующему уроку убедитесь, что:

- [ ] Node.js установлен и работает
- [ ] npm установлен и работает
- [ ] VS Code установлен с расширениями
- [ ] Git настроен и работает
- [ ] Создан тестовый проект
- [ ] Все команды выполняются без ошибок
- [ ] Порт 1337 свободен
- [ ] Система готова к работе с Strapi 