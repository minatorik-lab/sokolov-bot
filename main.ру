import telebot
import datetime

TOKEN = "8452746218:AAGBJMB8C_aHUvqZliHVWZ1JpHbCqLXqKZc"
bot = telebot.TeleBot(TOKEN)

EVENTS = {
    (1, 1): "1 января 1801 года было образовано Соединённое Королевство Великобритании и Ирландии.",
    (12, 25): "25 декабря 800 года Карл Великий был коронован императором Священной Римской империи.",
    (4, 12): "12 апреля 1961 года Юрий Гагарин стал первым человеком в космосе.",
    (7, 14): "14 июля 1789 года началась Французская революция — штурм Бастилии.",
    (11, 9): "9 ноября 1989 года пала Берлинская стена.",
}

DEFAULT = "В этот день произошло немало событий, которые история ещё не раскрыла полностью... 🔍"

@bot.message_handler(commands=['start'])
def start(message):
    bot.send_message(message.chat.id, 
    "👋 Добро пожаловать!\n\nЯ — бот профессора Соколова.\n\nОтправь мне дату в формате ДД.ММ и я расскажу что произошло в этот день в истории.\n\nНапример: 12.04")

@bot.message_handler(func=lambda m: True)
def handle_date(message):
    try:
        date = datetime.datetime.strptime(message.text.strip(), "%d.%m")
        key = (date.month, date.day)
        event = EVENTS.get(key, DEFAULT)
        bot.send_message(message.chat.id, 
        f"📅 {message.text.strip()}\n\n{event}\n\n📚 Подписывайся на канал профессора: t.me/professor_sokoloff")
    except:
        bot.send_message(message.chat.id, "Отправь дату в формате ДД.ММ, например: 12.04")

bot.polling()
