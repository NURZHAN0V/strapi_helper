# Практические задания: Установка и настройка Strapi

## Обзор практических заданий

В этом разделе вы выполните пошаговую установку Strapi CMS v5, создадите первый проект и настроите базовую конфигурацию. Все задания выполняются в порядке, указанном ниже.

**Время выполнения**: 60-90 минут  
**Сложность**: Начинающий  
**Требования**: Завершенный Урок 1.1

## 🎯 Задание 1: Установка Strapi через npx

### Цель
Установить Strapi CMS v5 используя рекомендуемый способ через npx.

### Пошаговое выполнение

#### Шаг 1: Подготовка рабочей директории
```bash
# Создайте папку для проектов Strapi
mkdir strapi-projects
cd strapi-projects

# Проверьте, что вы находитесь в правильной директории
pwd
```

#### Шаг 2: Создание проекта Strapi
```bash
# Создайте новый проект Strapi
npx create-strapi-app@latest my-first-strapi --quickstart
```

**Что происходит во время установки:**
- Скачивание последней версии Strapi
- Установка зависимостей
- Создание структуры проекта
- Настройка SQLite базы данных
- Запуск сервера разработки

#### Шаг 3: Ожидание завершения установки
Установка может занять 5-10 минут. Вы увидите прогресс в терминале:

```
Creating a new Strapi application at /path/to/my-first-strapi.
Installing dependencies:
- Installing packages (this might take a few minutes)
- Creating your first administrator
- Starting to create your Strapi application
```

#### Шаг 4: Создание первого администратора
После завершения установки откроется браузер. Создайте первого администратора:

1. **Имя**: Введите ваше имя
2. **Email**: Введите ваш email
3. **Пароль**: Создайте надежный пароль (минимум 8 символов)
4. **Подтвердите пароль**: Повторите пароль

#### Шаг 5: Проверка установки
После создания администратора вы попадете в админ-панель. Убедитесь, что:

- [ ] Сервер запущен на http://localhost:1337
- [ ] Админ-панель доступна по адресу http://localhost:1337/admin
- [ ] Вы можете войти с созданными учетными данными
- [ ] В админ-панели отображается приветственное сообщение

### ✅ Критерии проверки
- [ ] Проект создан успешно
- [ ] Сервер запущен без ошибок
- [ ] Админ-панель доступна
- [ ] Создан первый администратор
- [ ] Можно войти в систему

### 🔧 Если что-то не работает
**Проблема**: Ошибка "command not found: npx"
**Решение**: Убедитесь, что Node.js и npm установлены корректно

**Проблема**: Ошибка "port 1337 is already in use"
**Решение**: Остановите другие процессы на порту 1337 или измените порт

**Проблема**: Медленная установка
**Решение**: Проверьте интернет-соединение и попробуйте использовать VPN

---

## 🎯 Задание 2: Изучение структуры проекта

### Цель
Понять структуру созданного проекта Strapi и назначение основных файлов и папок.

### Пошаговое выполнение

#### Шаг 1: Остановка сервера
```bash
# В терминале с запущенным Strapi нажмите Ctrl+C
# Или откройте новый терминал и перейдите в папку проекта
cd my-first-strapi
```

#### Шаг 2: Изучение структуры проекта
```bash
# Просмотрите содержимое корневой папки
ls -la

# Изучите папку config
ls -la config/

# Изучите папку src
ls -la src/
```

#### Шаг 3: Анализ ключевых файлов

**package.json** - зависимости и скрипты:
```bash
cat package.json
```

**config/database.js** - настройки базы данных:
```bash
cat config/database.js
```

**config/server.js** - настройки сервера:
```bash
cat config/server.js
```

#### Шаг 4: Создание документации проекта
Создайте файл `PROJECT_STRUCTURE.md`:

```markdown
# Структура проекта my-first-strapi

## Основные папки:
- `config/` - конфигурационные файлы
- `src/` - исходный код
- `public/` - статические файлы
- `database/` - файлы базы данных SQLite

## Ключевые файлы:
- `package.json` - зависимости и скрипты
- `.env` - переменные окружения
- `config/database.js` - настройки БД
- `config/server.js` - настройки сервера

## Команды:
- `npm run develop` - запуск в режиме разработки
- `npm run start` - запуск в продакшене
- `npm run build` - сборка для продакшена
```

### ✅ Критерии проверки
- [ ] Понимание назначения основных папок
- [ ] Знание ключевых конфигурационных файлов
- [ ] Умение находить нужные файлы
- [ ] Создана документация проекта

---

## 🎯 Задание 3: Настройка базовой конфигурации

### Цель
Настроить основные параметры Strapi для вашего проекта.

### Пошаговое выполнение

#### Шаг 1: Настройка порта сервера
Откройте файл `config/server.js` и измените порт:

```javascript
module.exports = ({ env }) => ({
  host: env('HOST', '0.0.0.0'),
  port: env.int('PORT', 3000), // Измените с 1337 на 3000
  app: {
    keys: env.array('APP_KEYS'),
  },
});
```

#### Шаг 2: Настройка админ-панели
Откройте файл `config/admin.js` и добавьте настройки:

```javascript
module.exports = ({ env }) => ({
  auth: {
    secret: env('ADMIN_JWT_SECRET'),
  },
  apiToken: {
    salt: env('API_TOKEN_SALT'),
  },
  transfer: {
    token: {
      salt: env('TRANSFER_TOKEN_SALT'),
    },
  },
  flags: {
    nps: false,
    promoteEE: false,
  },
});
```

#### Шаг 3: Настройка API
Откройте файл `config/api.js` и настройте CORS:

```javascript
module.exports = ({ env }) => ({
  responses: {
    privateAttributes: ['_v', '__v', 'id', 'created_at'],
  },
  rest: {
    defaultLimit: 25,
    maxLimit: 100,
    withCount: true,
  },
});
```

#### Шаг 4: Создание файла .env
Создайте файл `.env` в корне проекта:

```env
# База данных
DATABASE_FILENAME=.tmp/data.db

# Сервер
HOST=0.0.0.0
PORT=3000

# Безопасность (замените на свои значения)
APP_KEYS=your-app-keys-1,your-app-keys-2
API_TOKEN_SALT=your-api-token-salt
ADMIN_JWT_SECRET=your-admin-jwt-secret
JWT_SECRET=your-jwt-secret
TRANSFER_TOKEN_SALT=your-transfer-token-salt

# Дополнительные настройки
NODE_ENV=development
```

#### Шаг 5: Перезапуск сервера
```bash
# Остановите сервер (Ctrl+C)
# Запустите заново
npm run develop
```

### ✅ Критерии проверки
- [ ] Порт изменен на 3000
- [ ] Файл .env создан с правильными настройками
- [ ] Сервер запускается на новом порту
- [ ] Админ-панель доступна по новому адресу

---

## 🎯 Задание 4: Создание тестового контента

### Цель
Создать первый тип контента и добавить тестовые данные для понимания работы Strapi.

### Пошаговое выполнение

#### Шаг 1: Вход в админ-панель
1. Откройте браузер
2. Перейдите по адресу http://localhost:3000/admin
3. Войдите с учетными данными администратора

#### Шаг 2: Создание типа контента "Article"
1. В левом меню найдите "Content-Type Builder"
2. Нажмите "Create new collection type"
3. Введите название "Article"
4. Добавьте следующие поля:
   - **Title** (Text, Short text)
   - **Content** (Text, Long text)
   - **Author** (Text, Short text)
   - **Published Date** (Date)
   - **Featured Image** (Media, Single media)
5. Сохраните тип контента

#### Шаг 3: Настройка прав доступа
1. Перейдите в "Settings" → "Users & Permissions plugin" → "Roles"
2. Выберите роль "Public"
3. Включите разрешения для Article:
   - find
   - findOne
4. Сохраните настройки

#### Шаг 4: Добавление тестовых статей
1. Перейдите в "Content Manager" → "Article"
2. Нажмите "Create new entry"
3. Заполните поля:
   - **Title**: "Моя первая статья в Strapi"
   - **Content**: "Это тестовый контент для изучения Strapi CMS..."
   - **Author**: "Ваше имя"
   - **Published Date**: Сегодняшняя дата
4. Сохраните и опубликуйте статью

#### Шаг 5: Проверка API
1. Откройте новый таб в браузере
2. Перейдите по адресу http://localhost:3000/api/articles
3. Убедитесь, что API возвращает созданную статью

### ✅ Критерии проверки
- [ ] Тип контента Article создан
- [ ] Настроены права доступа
- [ ] Добавлена тестовая статья
- [ ] API возвращает данные
- [ ] Статья отображается в админ-панели

---

## 🎯 Задание 5: Настройка Git репозитория

### Цель
Настроить Git для контроля версий проекта Strapi.

### Пошаговое выполнение

#### Шаг 1: Инициализация Git
```bash
# Перейдите в папку проекта
cd my-first-strapi

# Инициализируйте Git репозиторий
git init
```

#### Шаг 2: Создание .gitignore
Создайте файл `.gitignore`:

```gitignore
############################
# OS X
############################

.DS_Store
.AppleDouble
.LSOverride
Icon
.Spotlight-V100
.Trashes
._*

############################
# Linux
############################

*~

# temporary files which can be created if a process still has a handle open of a deleted file
.fuse_hidden*

# KDE directory preferences
.directory

# Linux trash folder which might appear on any partition or disk
.Trash-*

# .nfs files are created when an open file is removed but is still being accessed
.nfs*

############################
# Windows
############################

Thumbs.db
ehthumbs.db
Desktop.ini
$RECYCLE.BIN/
*.cab
*.msi
*.msm
*.msp
*.lnk

############################
# Packages
############################

*.7z
*.csv
*.dat
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip
*.com
*.class
*.dll
*.exe
*.o
*.seed
*.so
*.swo
*.swp
*.swn
*.swm
*.out
*.pid

############################
# Logs and databases
############################

.tmp
*.log
*.sql
*.sqlite
*.sqlite3

############################
# Misc.
############################

*#
ssl
.idea
nbproject
public/uploads/*
!public/uploads/.gitkeep

############################
# Node.js
############################

lib-cov
lcov.info
pids
logs
results
node_modules
.node

# Coverage directory used by tools like istanbul
coverage

# Grunt intermediate storage (http://gruntjs.com/creating-plugins#storing-task-files)
.grunt

# node-waf configuration
.lock-wscript

# Compiled binary addons (http://nodejs.org/api/addons.html)
build/Release

# Dependency directory
# https://www.npmjs.org/doc/misc/npm-faq.html#should-i-check-my-node_modules-folder-into-git-
node_modules

# Debug log from npm
npm-debug.log

############################
# Strapi
############################

.env
license.txt
exports
*.cache
dist
build
.strapi-updater.json

############################
# Custom
############################

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db
```

#### Шаг 3: Первый коммит
```bash
# Добавьте все файлы в Git
git add .

# Создайте первый коммит
git commit -m "Initial commit: Strapi project setup"
```

#### Шаг 4: Создание README.md
Создайте файл `README.md`:

```markdown
# My First Strapi Project

Это мой первый проект на Strapi CMS v5.

## Установка

```bash
npm install
```

## Запуск

### Режим разработки
```bash
npm run develop
```

### Продакшен
```bash
npm run build
npm run start
```

## Структура проекта

- `config/` - конфигурационные файлы
- `src/` - исходный код
- `public/` - статические файлы

## API

- Админ-панель: http://localhost:3000/admin
- API: http://localhost:3000/api
```

#### Шаг 5: Обновление репозитория
```bash
# Добавьте README.md
git add README.md
git commit -m "Add project documentation"
```

### ✅ Критерии проверки
- [ ] Git репозиторий инициализирован
- [ ] .gitignore настроен правильно
- [ ] Первый коммит создан
- [ ] README.md добавлен
- [ ] Проект готов к совместной работе

---

## 📋 Чек-лист завершения

Перед переходом к следующему уроку убедитесь, что:

### ✅ Обязательные пункты:
- [ ] Strapi установлен и работает
- [ ] Проект создан с именем "my-first-strapi"
- [ ] Сервер запущен на порту 3000
- [ ] Админ-панель доступна
- [ ] Создан первый администратор
- [ ] Понимание структуры проекта
- [ ] Настроена базовая конфигурация
- [ ] Создан тип контента Article
- [ ] Добавлена тестовая статья
- [ ] API работает корректно
- [ ] Git репозиторий настроен

### ✅ Дополнительные пункты:
- [ ] Изучены все конфигурационные файлы
- [ ] Создана документация проекта
- [ ] Настроены права доступа
- [ ] Проект готов к разработке

### ✅ Готовность к следующему уроку:
- [ ] Все задания выполнены
- [ ] Нет ошибок в системе
- [ ] Понимание основ Strapi
- [ ] Готовность к изучению админ-панели

---

## 🎉 Поздравления!

Вы успешно установили и настроили Strapi CMS v5! Теперь у вас есть рабочий проект с базовой конфигурацией.

**Следующий шаг**: Переходите к уроку 1.3 "Основы работы с админ-панелью", где вы изучите интерфейс Strapi и основные функции управления контентом.

---

## 📞 Поддержка

Если у вас возникли проблемы с выполнением заданий:

1. **Проверьте официальную документацию**: [Strapi Installation](https://docs.strapi.io/dev-docs/installation)
2. **Обратитесь к сообществу**: [Strapi Forum](https://forum.strapi.io/)
3. **Изучите FAQ** в конце урока
4. **Проверьте системные требования** на официальном сайте

**Удачи в изучении Strapi CMS!** 🚀 