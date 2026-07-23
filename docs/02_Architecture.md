# Architecture

## Иерархия

```text
Workspace
├── YouTube Channel
│   ├── Station
│   │   ├── Media Library
│   │   ├── Station Configuration
│   │   ├── Station State
│   │   ├── Playback Engine
│   │   └── Broadcast Lifecycle
│   └── Station
└── YouTube Channel
    └── Station
```

## Workspace

Корневой объект: каналы, общий Dashboard, Telegram, ресурсы, восстановление и системные события.

## YouTube Channel

Реальный канал YouTube: OAuth, YouTube API, плейлисты и общие параметры публикации.

## Station

Независимая рабочая единица: контент, подготовка LIVE, музыкальные циклы, запуск, остановка, состояние, восстановление и история.

## Broadcast

Отдельный экземпляр LIVE, получающий собственный неизменяемый пакет ресурсов.

## Media Library

Обработанные музыка, loop-видео, превью, названия и описания конкретной Station.

## Изоляция

Архитектура должна позволять независимо запускать, останавливать, восстанавливать и диагностировать каждую Station.

Конкретная реализация Worker, Scheduler, API и хранилища ещё не утверждена.
