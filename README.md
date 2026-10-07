# MONOLITH Custom Components

Коллекция кастомных React-компонентов, разработанных для платформы MONOLITH (архив и покупка билетов на выставки). 

Компоненты изначально создавались как Code Components для среды Framer, но здесь вынесены в чистый React/TypeScript формат для демонстрации навыков работы с DOM, состоянием и оптимизацией рендеринга.

## 🛠 Стек технологий
- **React** (Functional Components, Hooks)
- **TypeScript**
- **CSS** (Media Queries, CSS Variables, Keyframe Animations)
- **Browser APIs** (Intersection Observer, Touch Events, Scroll API)

## 📦 Компоненты

### 1. Menu (`Menu.tsx`)
Адаптивное полноэкранное меню с плавной анимацией появления.
**Технические особенности:**
- Отслеживание скролла через `window.scrollY` с пассивным слушателем (`passive: true`) для производительности.
- Блокировка скролла основной страницы (`document.body.style.overflow`) при открытом меню.
- Реализация нативного свайп-жеста (swipe-to-close) через `onTouchStart` и `onTouchMove` с использованием `useRef`.
- Плавный скролл к якорям (`scrollIntoView`) с обработкой маршрутизации.

### 2. ScrollToTop (`ScrollToTop.tsx`)
Кнопка возврата к началу страницы, которая динамически меняет цвет иконки в зависимости от фона секции под ней.
**Технические особенности:**
- Использование **Intersection Observer API** вместо слушателя скролла для определения видимости секции `#contacts` (оптимизация производительности).
- Динамическая смена цвета через CSS-переменные (`--icon-color`) и inline-стили TypeScript (`React.CSSProperties`).
- Безопасное обращение к DOM через опциональную цепочку (`?.`).

### 3. RunText / Marquee (`run_text.tsx`)
Бесконечная бегущая строка с текстом.
**Технические особенности:**
- Анимация через CSS `@keyframes` с использованием свойства `will-change: transform` для выноса анимации на уровень композитинга (GPU-ускорение).
- Динамическое дублирование контента через `Array.from` для создания бесшовного цикла.
- Полная адаптивность типографики и высоты контейнера через `@media` запросы.

## Использование

Эти компоненты самодостаточны (содержат встроенные стили через тег `<style>` для простоты переноса в Framer), но в классическом React-проекте стили рекомендуется вынести в отдельные `.css` или `.module.css` файлы.

```tsx
import Menu from './components/Menu'
import ScrollToTop from './components/ScrollToTop'
import RunText from './components/run_text'

function App() {
  return (
    <>
      <Menu />
      <RunText />
      {/* Основной контент */}
      <ScrollToTop />
    </>
  )
}
