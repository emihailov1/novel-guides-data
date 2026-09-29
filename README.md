# novel-guides-data

Удалённые данные для приложений Novel Guides (GitHub Pages). Приложение на старте: сеть → кэш → встроенный пак.

```
/<gameId>/manifest.json    { "version": N, "files": { "<путь>": <версия файла> } }
/<gameId>/schedule.json    { "items": [{ "date": "ГГГГ-ММ-ДД", "title": "...", "story": "<storyId>", "note": "..." }] }
/<gameId>/promo.json       { "codes": [{ "code": "...", "reward": "...", "until": "ГГГГ-ММ-ДД", "source": "https://..." }] }
/<gameId>/episodes/*.json  новые и исправленные серии (подменяют встроенные по id)
/<gameId>/stories/*.json   истории (новые серии в списке сезонов)
```

Файлы контента публикуются из основного репозитория: `py -3.12 tool/data_sync.py <game> episodes/<id>.json`.
Скрипт копирует файл, поднимает версии и проверяет пак. Приложение скачивает только файлы с выросшей версией
и сохраняет их, только если пак после них проходит проверку.
