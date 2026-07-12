# Слайд 3

## Текст для слайда (копировать в PPT)

Архитектура Avalonia

Application → Window → Controls → Rendering

Application
Управляет жизненным циклом приложения
Хранит глобальные ресурсы и стили
Определяет точку входа (главное окно)

## Схема

graph TD
    Win["🪟 Window"]
    OS["🖥️ Оконный менеджер ОС<br/>заголовок, границы, resize"]
    Content["📦 Content<br/>корневое визуальное дерево"]
    Events["⚡ Системные события<br/>Closing, Activated, Resized"]

    Win --> OS
    Win --> Content
    Win --> Events

    classDef winStyle fill:#6C63FF,stroke:#4B3FCF,stroke-width:3px,color:#fff,rx:12,ry:12
    classDef childStyle fill:#B8B2FF,stroke:#8E85FF,stroke-width:2px,color:#222,rx:10,ry:10

    class Win winStyle
    class OS,Content,Events childStyle
## Заметки лектора

Application — единственный экземпляр на приложение (singleton), точка входа — метод OnFrameworkInitializationCompleted.

Жизненный цикл: Initialize → OnFrameworkInitializationCompleted → показ главного окна → работа приложения → завершение (Shutdown).

Application.Resources — глобальный словарь ресурсов (цвета, стили, шаблоны), доступный из любого View через StaticResource/DynamicResource.

В App.axaml обычно подключают тему (Fluent, Default) и глобальные стили через `<Application.Styles>`.

Различие desktop/mobile точки входа: для desktop — ClassicDesktopStyleApplicationLifetime (создаёт Window), для мобильных — SingleViewApplicationLifetime (создаёт единственный View без окна).
