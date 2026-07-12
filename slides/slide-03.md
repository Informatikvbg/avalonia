# Слайд 3

## Текст для слайда (копировать в PPT)

Архитектура Avalonia

Application → Window → Controls → Rendering

Application
Управляет жизненным циклом приложения
Хранит глобальные ресурсы и стили
Определяет точку входа (главное окно)

## Схема

```mermaid
graph TD
    App["⚙️ Application"]
    Life["🔄 Жизненный цикл"]
    Res["🎨 Глобальные ресурсы и стили"]
    Entry["🚪 Точка входа"]

    App --> Life
    App --> Res
    App --> Entry

    classDef appStyle fill:#4B3FCF,stroke:#2E2470,stroke-width:3px,color:#fff,rx:12,ry:12
    classDef childStyle fill:#8E85FF,stroke:#6C63FF,stroke-width:2px,color:#fff,rx:10,ry:10

    class App appStyle
    class Life,Res,Entry childStyle
```

## Заметки лектора

Application — единственный экземпляр на приложение (singleton), точка входа — метод OnFrameworkInitializationCompleted.

Жизненный цикл: Initialize → OnFrameworkInitializationCompleted → показ главного окна → работа приложения → завершение (Shutdown).

Application.Resources — глобальный словарь ресурсов (цвета, стили, шаблоны), доступный из любого View через StaticResource/DynamicResource.

В App.axaml обычно подключают тему (Fluent, Default) и глобальные стили через `<Application.Styles>`.

Различие desktop/mobile точки входа: для desktop — ClassicDesktopStyleApplicationLifetime (создаёт Window), для мобильных — SingleViewApplicationLifetime (создаёт единственный View без окна).
