# 📖 Описание библиотеки

DSErrorsGenerator создана для упрощения создания сообщений об ошибках. Библиотека автоматически генерирует Embed с текстом ошибки, и отправляет его.

# ⚙️ Параметры

Параметр | Тип | Обязательный | Стандартное значение | Информация |
--- | --- | --- | --- |---
ctx | `discord.ext.commands.Context` | Да | `None` | Используется для автоматической отправки сообщения.
Title | `Строка (str)` | Нет | `Ошибка!` | Заголовок эмбеда, сообщающий об ошибке.
Description | `Строка (str)` | Да | `None` | Описание ошибки.
Color | `Число (int)` | Нет | `0xFF0000 (Красный)` | Цвет эмбеда.
Emoji | `Строка (str)` | Нет | `❌` | Смайл в заголовке.
Code | `Число (int)` | Нет | `None` | Код ошибки (если имеется). Находится ниже описания ошибки.
Footer | `Строка (str)` | Нет | `None` | Футер эмбеда.

# ❌ Ошибки

Ошибка | Информация
--- | --- 
`MissingArgument` | Вызывается, когда был упущен один из обязательных аргументов (Description и ctx).
`BadObjectType` | Вызывается, когда тип объекта не соответствует ожидаемому.
`MissingEmoji` | Вызывается, когда в объекте Emoji отсутствует какой-либо смайл.

# 🛠️ Функции

Название | Тип | Что делает
--- | --- | ---
`send_error()` | Coroutine | Используется для генерации и отправки Embed сообщения.
`generate_error()` | Coroutine | Используется для генерации Embed сообщения. Рекомендуется, если вы хотите внести какие-либо дополнительные изменения.

В аргументы каждой функции необходимо передать `ctx`

# 💡 Примеры использования

Импорт:
```py
from DSErrorsGenerator import ErrorGenerator
```

Использование функции:
```py
await ErrorGenerator(<Arguments>).function(ctx)
```

Пример кода:
```py
import discord
from discord.ext import commands

from DSErrorsGenerator import ErrorGenerator as Eg

bot = commands.Bot(command_prefix="!")

@bot.event
async def on_ready():
    print(f"[{bot.user}] Ready!")

@bot.command()
async def error(ctx):
    await Eg(ctx, description="Это пример ошибки.").send_error(ctx)

bot.run("token")
```

Вывод:

![First example of russian documentation](screenshots/example-ru-1.png)

Далее будем рассматривать на примере одной команды, дабы не делать документацию огромной.

Передадим все существующие аргументы:
```py
@bot.command()
async def error(ctx):
    await Eg(ctx, description="Это пример ошибки.", title="Возникла ошибка!", color=0x00FF00, code=78, emoji="💢", footer="Администраторы уже решают проблему.").send_error(ctx)
```

Вывод:

![Second example of russian documentation](screenshots/example-ru-2.png)
