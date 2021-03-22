# ⚙️ DSErrorsGenerator
DSErrorsGenerator создана для упрощения создания сообщений о пользовательских ошибках. / DSErrorsGenerator designed to simplify the creation of user error messages.

![](https://img.shields.io/badge/version-0.0.1-red)
![](https://img.shields.io/badge/python->=_3.8-blue)
![](https://img.shields.io/badge/discord.py->=_1.5-blue)
![](https://img.shields.io/badge/emoji->=_1.2-blue)

## ⬇️ Установка / Install
```python
pip install DSErrorsGenerator
```

## 📚 Документация / Documentation
[![](https://img.shields.io/badge/-Документация_на_Русском-2f3136?style=for-the-badge&logo=books)](https://github.com/FeeFort/discord-error-generator/blob/main/documentation-ru.md)
[![](https://img.shields.io/badge/-Documentation_on_English-2f3136?style=for-the-badge)](https://github.com/FeeFort/discord-error-generator/blob/main/documentation-en.md)

## 💻 Пример кода / Example of the code
```py
@bot.command()
async def error(ctx):
    await Eg(description="This is example of error.", lang="en").send_error(ctx)
```
![](screenshots/example-en-1.png)

## 🤙 Подать идею для развития / Submit an idea for development
[![](https://img.shields.io/badge/-мой_дискорд-2f3136?style=for-the-badge&logo=Discord)](https://discord.com/users/435463855250866176)
