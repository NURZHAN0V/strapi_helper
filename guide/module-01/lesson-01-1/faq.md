# FAQ: Подготовка среды разработки

## Общие вопросы

### Q: Какая версия Node.js нужна для Strapi v5?
**A**: Strapi v5 требует Node.js версии 18 или выше. Рекомендуется использовать LTS (Long Term Support) версию для стабильности. На момент создания руководства актуальной является версия 22.x.

### Q: Можно ли использовать Yarn вместо npm?
**A**: Да, Strapi поддерживает как npm, так и Yarn. Выберите тот пакетный менеджер, с которым вам удобнее работать. В этом руководстве мы используем npm, но все команды можно адаптировать для Yarn.

### Q: Какой редактор кода лучше использовать?
**A**: Рекомендуется использовать VS Code, так как он бесплатный, имеет отличную поддержку JavaScript/TypeScript и множество полезных расширений. Однако вы можете использовать любой редактор, который вам нравится.

### Q: Нужен ли Git для работы с Strapi?
**A**: Git не обязателен для работы с Strapi, но настоятельно рекомендуется для контроля версий и совместной работы. Это стандарт в современной разработке.

---

## Установка и настройка

### Q: Что делать, если Node.js не устанавливается?
**A**: 
1. Убедитесь, что у вас есть права администратора
2. Попробуйте скачать установщик с официального сайта nodejs.org
3. Для Windows: используйте установщик .msi
4. Для macOS: используйте Homebrew или официальный установщик
5. Для Linux: используйте менеджер пакетов вашего дистрибутива

### Q: Как проверить, что Node.js установлен правильно?
**A**: Откройте терминал и выполните:
```bash
node --version
npm --version
```
Если команды возвращают версии, значит установка прошла успешно.

### Q: Что делать, если версия Node.js ниже требуемой?
**A**: 
1. **Windows**: Скачайте новую версию с nodejs.org и переустановите
2. **macOS**: `brew update && brew upgrade node`
3. **Linux**: Обновите через менеджер пакетов или используйте nvm

### Q: Как установить nvm (Node Version Manager)?
**A**: 
**Windows**: Скачайте nvm-windows с GitHub
**macOS/Linux**: 
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```

---

## VS Code

### Q: Какие расширения VS Code нужны для работы с Strapi?
**A**: Основные расширения:
- **ES7+ React/Redux/React-Native snippets** - для быстрого написания кода
- **Prettier - Code formatter** - для форматирования кода
- **ESLint** - для проверки качества кода
- **GitLens** - для работы с Git
- **Auto Rename Tag** - для работы с JSX/HTML
- **Bracket Pair Colorizer** - для лучшей читаемости кода

### Q: Как настроить автоформатирование в VS Code?
**A**: 
1. Установите расширение Prettier
2. Откройте настройки (Ctrl+,)
3. Найдите "format on save" и включите
4. Установите Prettier как форматтер по умолчанию

### Q: VS Code работает медленно, что делать?
**A**: 
1. Отключите ненужные расширения
2. Увеличьте объем памяти для VS Code
3. Используйте workspace settings вместо глобальных
4. Регулярно перезапускайте VS Code

---

## Git

### Q: Как настроить Git впервые?
**A**: 
```bash
git config --global user.name "Ваше Имя"
git config --global user.email "ваш@email.com"
```

### Q: Что такое .gitignore и зачем он нужен?
**A**: .gitignore - это файл, который указывает Git, какие файлы и папки не нужно отслеживать. Для Strapi проектов важно исключить:
- node_modules/ (зависимости)
- .env (переменные окружения)
- build/ (собранные файлы)
- .cache/ (кэш)

### Q: Как создать .gitignore для Strapi проекта?
**A**: Создайте файл .gitignore в корне проекта со следующим содержимым:
```gitignore
# Dependencies
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Strapi
.env
.tmp/
.cache/
build/
dist/
exports/
*.cache

# OS
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
*.swp
*.swo
```

---

## Проблемы и решения

### Q: Команда "node" не найдена
**A**: 
1. Проверьте, что Node.js установлен
2. Перезапустите терминал
3. Проверьте переменную PATH
4. Попробуйте переустановить Node.js

### Q: Ошибка "EACCES: permission denied"
**A**: 
1. **Windows**: Запустите терминал от имени администратора
2. **macOS/Linux**: Используйте sudo или настройте права доступа
3. **Альтернатива**: Используйте nvm для управления версиями Node.js

### Q: npm устанавливает пакеты очень медленно
**A**: 
1. Проверьте скорость интернета
2. Попробуйте другой npm registry
3. Используйте yarn вместо npm
4. Очистите кэш npm: `npm cache clean --force`

### Q: VS Code не видит установленные расширения
**A**: 
1. Перезапустите VS Code
2. Проверьте, что расширения установлены в правильную папку
3. Попробуйте переустановить расширения
4. Проверьте настройки VS Code

---

## Системные требования

### Q: Какие минимальные системные требования для Strapi?
**A**: 
- **ОС**: Windows 10+, macOS 10.14+, Ubuntu 18.04+
- **RAM**: Минимум 2GB, рекомендуется 4GB+
- **Диск**: Минимум 1GB свободного места
- **Процессор**: Любой современный процессор

### Q: Можно ли использовать Strapi на виртуальной машине?
**A**: Да, Strapi можно использовать на виртуальной машине. Убедитесь, что у VM достаточно ресурсов (минимум 2GB RAM, 1GB диска).

### Q: Работает ли Strapi на ARM процессорах (Apple M1/M2)?
**A**: Да, Strapi поддерживает ARM архитектуру. Node.js и все зависимости работают на ARM процессорах.

---

## Производительность

### Q: Как ускорить работу VS Code?
**A**: 
1. Отключите ненужные расширения
2. Используйте workspace settings
3. Увеличьте объем памяти для VS Code
4. Регулярно перезапускайте редактор

### Q: npm работает медленно, что делать?
**A**: 
1. Используйте yarn вместо npm
2. Настройте npm cache
3. Используйте быстрый интернет
4. Попробуйте другой npm registry

### Q: Как оптимизировать работу с Git?
**A**: 
1. Используйте .gitignore для исключения ненужных файлов
2. Делайте частые, но небольшие коммиты
3. Используйте Git LFS для больших файлов
4. Настройте Git aliases для часто используемых команд

---

## Дополнительные вопросы

### Q: Нужно ли изучать JavaScript перед работой с Strapi?
**A**: Базовые знания JavaScript необходимы для работы с Strapi. Рекомендуется изучить:
- Переменные и типы данных
- Функции и объекты
- Асинхронное программирование
- ES6+ синтаксис

### Q: Какой базы данных знаний достаточно для начала?
**A**: Для начала работы с Strapi достаточно базовых знаний:
- Основы веб-разработки
- Базовый JavaScript
- Понимание REST API
- Основы работы с базами данных

### Q: Можно ли использовать Strapi без знания программирования?
**A**: Strapi - это headless CMS, который требует базовых знаний программирования. Для простых проектов можно использовать админ-панель, но для кастомизации потребуется знание JavaScript.

---

## Полезные ресурсы

### Официальная документация
- [Strapi Documentation](https://docs.strapi.io/)
- [Node.js Documentation](https://nodejs.org/docs/)
- [VS Code Documentation](https://code.visualstudio.com/docs)
- [Git Documentation](https://git-scm.com/doc)

### Сообщество
- [Strapi Forum](https://forum.strapi.io/)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/strapi)
- [GitHub Discussions](https://github.com/strapi/strapi/discussions)

### Видео-уроки
- [Strapi YouTube Channel](https://www.youtube.com/c/Strapi)
- [Node.js Tutorials](https://nodejs.org/en/learn/)
- [VS Code Tutorials](https://code.visualstudio.com/learn)

---

## Контакты для поддержки

Если у вас остались вопросы, которые не покрыты в этом FAQ:

1. **Проверьте официальную документацию** Strapi
2. **Обратитесь к сообществу** на форуме Strapi
3. **Изучите GitHub Issues** для известных проблем
4. **Создайте новый вопрос** на Stack Overflow

**Удачи в изучении Strapi CMS!** 🚀 