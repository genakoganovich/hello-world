name: Hello World                    # ← Название workflow (видно в вкладке Actions репозитория)
                                     #   Помогает отличать от других задач.

on: [push]                           # ← ТРИГГЕР: Когда запускать?
                                     #   [push] = при пуше (commit+push) в main/master ветку.
                                     #   Можно добавить [pull_request] или schedule (по расписанию).
                                     #   Комментарий # — игнорируется, для людей.

jobs:                                # ← СЕКЦИЯ ЗАДАНИЙ (jobs). Можно несколько jobs параллельно.
  greet:                             # ← Имя задания (job). "greet" = приветствие.
    runs-on: ubuntu-latest           # ← Где запускать? На виртуальной машине Ubuntu (новейшая версия).
                                     #   Бесплатно от GitHub. Альтернативы: windows-latest, macos-latest.

    steps:                           # ← ШАГИ (steps) внутри job. Выполняются по порядку, как команды в терминале.
      - uses: actions/checkout@v4    # Шаг 1: Готовое действие (action) от GitHub.
                                     #   "actions/checkout@v4" = скачай весь код репозитория в рабочую папку.
                                     #   @v4 = версия 4. Без этого код не будет доступен!

      - run: echo "Hello, World!"    # Шаг 2: Выполни shell-команду (run).
                                     #   "echo" = вывести текст в лог. На Ubuntu/Linux терминале.
                                     #   Можно npm install, python test.py и т.д.