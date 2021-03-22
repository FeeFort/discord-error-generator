# 📖 Описание библиотеки

DSErrorsGenerator создана для упрощения создания сообщений о пользовательских ошибках. Библиотека автоматически генерирует Embed с текстом ошибки, и отправляет его.

# ⚙️ Параметры

Параметр | Тип | Обязательный | Стандартное значение | Информация |
--- | --- | --- | --- |---
Title | `Строка (str)` | Нет | `Ошибка!` | Заголовок эмбеда, сообщающий об ошибке.
Description | `Строка (str)` | Да | `None` | Описание ошибки.
Color | `Число (int)` | Нет | `0xFF0000 (Красный)` | Цвет эмбеда.
Emoji | `Строка (str)` | Нет | `❌` | Смайл в заголовке.
Code | `Число (int)` | Нет | `None` | Код ошибки (если имеется). Находится ниже описания ошибки.
Footer | `Строка (str)` | Нет | `None` | Футер эмбеда.
Lang (Language) | `Строка (str)` | Да | `None` | Язык ошибки. Доступные значения: `ru` и `en`.

# ❌ Ошибки

Ошибка | Информация
--- | --- 
`MissingArgument` | Вызывается, когда был упущен один из обязательных аргументов (Description и Lang).
`BadObjectType` | Вызывается, когда тип объекта не соответствует ожидаемому.
`MissingEmoji` | Вызывается, когда в объекте Emoji отсутствует какой-либо смайл.
`BadLanguage` | Вызывается, когда был указан неверный язык.

# 🛠️ Функции

Название | Тип | Что делает
--- | --- | ---
`send_error()` | Coroutine | Используется для генерации и отправки Embed сообщения.
`generate_error()` | Coroutine | Используется для генерации Embed сообщения. Рекомендуется, если вы хотите внести какие-либо дополнительные изменения.

В аргументы функции `send_error()` необходимо передать `ctx`

# 💡 Примеры использования

Импорт:
```py
from DSErrorsGenerator import ErrorGenerator
```

Использование функции:
```py
await ErrorGenerator(description="Здесь вы можете описать ошибку.", lang="ru", <Other arguments>).function()
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
    await Eg(description="Это пример ошибки.", lang="ru").send_error(ctx)  # Обратите внимание на то, что в аргументы функции send_error() я передал ctx.

bot.run("token")
```

![First example of russian documentation](screenshots/example-ru-1.png)

Функция `generate_error()`:
```py
@bot.command()
async def error(ctx):
    url = "https://bit.ly/316XG00"
    embed = await Eg(description="Это пример ошибки.", lang="ru").generate_error()  # Здесь я использую другую функцию, поэтому передавать ctx в аргументы функции не нужно.
    embed.set_image(url=url)  # Внёс небольшие поправки в Embed - поставил image.
    await ctx.send(embed = embed)
```

![Second example of russian documentation](screenshots/example-ru-3.png)

Передадим все существующие аргументы:
```py
@bot.command()
async def error(ctx):
    await Eg(description="Это пример ошибки.", lang="ru", title="Возникла ошибка!", color=0x00FF00, code=78, emoji="💢", footer="Администраторы уже решают эту проблему.").send_error(ctx)
```

Вывод:

![Third example of russian documentation](screenshots/example-ru-2.png)
