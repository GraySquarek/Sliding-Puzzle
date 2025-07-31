# 🚀 Инструкции по деплою

Этот документ содержит инструкции по развертыванию игры "Пятнашки" на различных платформах.

## 📋 Предварительные требования

- Node.js версии 14.0 или выше
- npm или yarn
- Git репозиторий с кодом проекта

## 🔧 Локальная сборка

### 1. Установка зависимостей
```bash
npm install
```

### 2. Сборка для продакшена
```bash
npm run build
```

### 3. Тестирование продакшен сборки
```bash
npm run prod
```

## 🌐 Деплой на GitHub Pages

### Автоматический деплой (рекомендуется)

1. **Создайте репозиторий на GitHub**
2. **Настройте GitHub Pages:**
   - Перейдите в Settings → Pages
   - Выберите Source: "Deploy from a branch"
   - Выберите Branch: "gh-pages"
   - Нажмите Save

3. **Обновите homepage в package.json:**
   ```json
   {
     "homepage": "https://yourusername.github.io/your-repo-name"
   }
   ```

4. **Установите gh-pages:**
   ```bash
   npm install --save-dev gh-pages
   ```

5. **Деплой:**
   ```bash
   npm run deploy
   ```

### Ручной деплой

1. Соберите проект: `npm run build`
2. Создайте ветку gh-pages: `git checkout -b gh-pages`
3. Добавьте файлы: `git add build/*`
4. Зафиксируйте: `git commit -m "Deploy to GitHub Pages"`
5. Отправьте: `git push origin gh-pages`

## 🚀 Деплой на Netlify

### Через Netlify CLI

1. **Установите Netlify CLI:**
   ```bash
   npm install -g netlify-cli
   ```

2. **Войдите в аккаунт:**
   ```bash
   netlify login
   ```

3. **Инициализируйте проект:**
   ```bash
   netlify init
   ```

4. **Деплой:**
   ```bash
   netlify deploy --prod
   ```

### Через веб-интерфейс

1. Зайдите на [netlify.com](https://netlify.com)
2. Нажмите "New site from Git"
3. Подключите ваш GitHub репозиторий
4. Настройте:
   - Build command: `npm run build`
   - Publish directory: `build`
5. Нажмите "Deploy site"

## ⚡ Деплой на Vercel

### Через Vercel CLI

1. **Установите Vercel CLI:**
   ```bash
   npm install -g vercel
   ```

2. **Войдите в аккаунт:**
   ```bash
   vercel login
   ```

3. **Деплой:**
   ```bash
   vercel --prod
   ```

### Через веб-интерфейс

1. Зайдите на [vercel.com](https://vercel.com)
2. Нажмите "New Project"
3. Подключите ваш GitHub репозиторий
4. Нажмите "Deploy"

## 🔧 Настройка переменных окружения

### Для продакшена

Создайте файл `.env.production`:
```env
GENERATE_SOURCEMAP=false
REACT_APP_VERSION=$npm_package_version
```

### Для разработки

Создайте файл `.env.development`:
```env
REACT_APP_API_URL=http://localhost:3000
REACT_APP_DEBUG=true
```

## 📱 PWA настройки

Для включения PWA функциональности:

1. **Обновите manifest.json** с вашими данными
2. **Добавьте иконки** в папку public/
3. **Настройте service worker** (опционально)

## 🔍 Оптимизация производительности

### Перед деплоем

1. **Проверьте размер бандла:**
   ```bash
   npm run build
   # Проверьте размер папки build/
   ```

2. **Оптимизируйте изображения:**
   - Используйте WebP формат
   - Сжимайте изображения
   - Используйте lazy loading

3. **Включите сжатие:**
   - Gzip для статических файлов
   - Brotli для современных браузеров

## 🐛 Отладка

### Локальная отладка

```bash
# Запуск в режиме разработки
npm start

# Запуск тестов
npm test

# Проверка линтером
npm run lint
```

### Продакшен отладка

1. Проверьте консоль браузера
2. Проверьте Network tab
3. Используйте Lighthouse для аудита

## 📊 Мониторинг

### Рекомендуемые инструменты

- **Google Analytics** - для отслеживания пользователей
- **Sentry** - для отслеживания ошибок
- **Lighthouse CI** - для автоматической проверки производительности

## 🔒 Безопасность

### Рекомендации

1. **HTTPS** - используйте только HTTPS в продакшене
2. **CSP** - настройте Content Security Policy
3. **CORS** - настройте Cross-Origin Resource Sharing
4. **Заголовки безопасности** - добавьте security headers

### Пример заголовков для Netlify

Создайте файл `public/_headers`:
```
/*
  X-Frame-Options: DENY
  X-XSS-Protection: 1; mode=block
  X-Content-Type-Options: nosniff
  Referrer-Policy: strict-origin-when-cross-origin
  Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline';
```

## 📞 Поддержка

Если у вас возникли проблемы с деплоем:

1. Проверьте логи сборки
2. Убедитесь, что все зависимости установлены
3. Проверьте версию Node.js
4. Создайте Issue в репозитории

---

**Удачного деплоя! 🚀** 