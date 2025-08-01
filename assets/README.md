# 📁 Медиафайлы проекта

## Обзор

Папка `assets/` содержит все медиафайлы, используемые в руководстве по Strapi CMS v5. Здесь хранятся изображения, видео и документы, которые помогают лучше понять материал.

## 📂 Структура папок

```
assets/
├── README.md                    # Этот файл
├── images/                      # Изображения
│   ├── screenshots/             # Скриншоты интерфейса
│   │   ├── admin-panel/         # Админ-панель Strapi
│   │   ├── content-manager/     # Content Manager
│   │   ├── content-builder/     # Content-type Builder
│   │   └── settings/            # Настройки и конфигурация
│   ├── diagrams/                # Диаграммы и схемы
│   │   ├── architecture/        # Архитектурные схемы
│   │   ├── workflows/           # Рабочие процессы
│   │   └── data-flow/           # Потоки данных
│   ├── examples/                # Примеры проектов
│   │   ├── blog/                # Пример блога
│   │   ├── ecommerce/           # Пример магазина
│   │   └── portfolio/           # Пример портфолио
│   └── icons/                   # Иконки и логотипы
│       ├── strapi/              # Логотипы Strapi
│       ├── tools/               # Иконки инструментов
│       └── concepts/            # Иконки концепций
├── videos/                      # Видео материалы
└── docs/                        # Документы (PDF, схемы)
```

## 🎯 Назначение каждого раздела

### 📸 Screenshots (Скриншоты)
Скриншоты интерфейса Strapi для демонстрации:
- **admin-panel/**: Главная панель, навигация, дашборд
- **content-manager/**: Управление контентом, создание записей
- **content-builder/**: Создание типов контента, настройка полей
- **settings/**: Настройки безопасности, плагинов, API

### 📊 Diagrams (Диаграммы)
Визуальные схемы и диаграммы:
- **architecture/**: Архитектура Strapi, компоненты системы
- **workflows/**: Рабочие процессы, последовательности действий
- **data-flow/**: Потоки данных, API взаимодействия

### 💡 Examples (Примеры)
Примеры реальных проектов:
- **blog/**: Структура блога, типы контента
- **ecommerce/**: Магазин, товары, заказы
- **portfolio/**: Портфолио, проекты, работы

### 🎨 Icons (Иконки)
Иконки и логотипы:
- **strapi/**: Официальные логотипы Strapi
- **tools/**: Иконки инструментов разработки
- **concepts/**: Иконки для объяснения концепций

## 📏 Рекомендации по файлам

### Форматы файлов:
- **Изображения**: PNG, JPG, SVG
- **Видео**: MP4, WebM
- **Документы**: PDF, SVG

### Размеры:
- **Скриншоты**: 1200-1600px ширина
- **Диаграммы**: SVG (вектор) или PNG
- **Иконки**: 32x32px или SVG
- **Примеры**: до 800px ширина

### Именование:
- Используйте описательные имена: `admin-panel-dashboard.png`
- Разделяйте слова дефисами
- Указывайте версию если нужно: `strapi-v5-logo.svg`

## 🔗 Использование в Markdown

### Скриншоты:
```markdown
![Админ-панель Strapi](../assets/images/screenshots/admin-panel/dashboard.png)
```

### Диаграммы:
```markdown
![Архитектура Strapi](../assets/images/diagrams/architecture/strapi-architecture.png)
```

### Примеры:
```markdown
![Пример блога](../assets/images/examples/blog/blog-structure.png)
```

### Иконки:
```markdown
![Логотип Strapi](../assets/images/icons/strapi/strapi-logo.svg)
```

## 📋 Правила добавления файлов

1. **Размещайте файлы в соответствующих папках**
2. **Используйте описательные имена файлов**
3. **Оптимизируйте размер файлов для веба**
4. **Добавляйте alt-текст в Markdown**
5. **Обновляйте этот README при добавлении новых разделов**

## 🤝 Вклад в медиафайлы

Если у вас есть:
- Качественные скриншоты интерфейса
- Полезные диаграммы и схемы
- Примеры проектов
- Иконки и логотипы

Поделитесь ими с сообществом!

---

**Статус**: Готово к использованию  
**Последнее обновление**: Июль 2025 