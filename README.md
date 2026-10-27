# POLITDYNASTY Content

Контент-манифест лаунчера **POLITDYNASTY**: новости, каталог модов и обновления самого лаунчера.

## Как это работает

Лаунчере при старте (и по кнопке «Проверить обновления») загружает файл `manifest.json`
с raw.githubusercontent.com, кэширует его локально (ETag) и предлагает:

- **обновление лаунчера** — если версия в манифсте новее текущей: скачивает установщик
  из GitHub Releases и проверяет SHA-256 перед запуском;
- **новости** — блок на главной и страница «Новости»;
- **моды** — раздел «Моды»: установка одним кликом с проверкой контрольной суммы.

## Формат манифеста

| Поле | Назначение |
| --- | --- |
| `launcher.version` | Последняя версия лаунчера (семантика `x.y.z`) |
| `launcher.url` | Ссылка на установщик в GitHub Releases |
| `launcher.sha256` | Контрольная сумма установщика |
| `news[]` | Новости: `id`, `title`, `date`, `text` |
| `mods[]` | Моды: `id`, `name`, `version`, `url`, `sha256`, `sizeBytes`, `gameVersion` |

## Как обновить контент

1. Положи новый файл мода в `mods/` (для лаунчера — новый Release с установщиком).
2. Посчитай сумму: `Get-FileHash файл -Algorithm SHA256`.
3. Обнови `manifest.json` (версии, ссылки, суммы).
4. Запушь: `git push`.

Лаунчер подхватит изменения при следующей проверке.

## Ссылки

- Репозиторий: https://github.com/awkdkawdkawk/politdynasty-content
- Манифест: https://raw.githubusercontent.com/awkdkawdkawk/politdynasty-content/main/manifest.json
