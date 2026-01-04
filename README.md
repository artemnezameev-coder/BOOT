import telebot
from telebot import types

bot = telebot.TeleBot('8206455435:AAHXLAHbU77U1XBLrqDVtBW781lNz3vLsOA')

@bot.message_handler(commands=['start'])
def start(message):
    markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
    btn1 = types.KeyboardButton('Перейти к задачам')
    btn2 = types.KeyboardButton('ОГЭ')
    btn3 = types.KeyboardButton('ИИ асистенты')
    markup.row(btn1)
    markup.row(btn2, btn3)

    bot.send_message(message.chat.id, 'Привет', reply_markup=markup)

@bot.message_handler(func=lambda m: m.text == 'Перейти к задачам')
def on_click(message):
    markup = types.InlineKeyboardMarkup()
    btn1 = types.InlineKeyboardButton('Тепловые явления', url='https://phys-oge.sdamgia.ru/test?theme=37')
    btn2 = types.InlineKeyboardButton('Электричество ', url = 'https://sphksev.ru/wp-content/uploads/2020/04/P-10-Fizika.-Sila-toka.-Reshenie-zadach-na-30.04.2020.pdf')
    btn3 = types.InlineKeyboardButton('Импульс, закон сохранения импульса ', url = 'https://phys-oge.sdamgia.ru/search?keywords=1&cb=1&search=1.15%20Закон%20сохранения%20импульса%20для%20замкнутой%20системы%20тел.')
    btn4 = types.InlineKeyboardButton('Магнит ', url ='https://phys-oge.sdamgia.ru/test?theme=12')
    btn5 = types.InlineKeyboardButton('Свет', url = 'https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://phys-ege.sdamgia.ru/test%3Ftheme%3D253&ved=2ahUKEwjY2a_b2fGRAxXmGRAIHT5dD_8QFnoECBsQAQ&usg=AOvVaw2nwDD69925QfC7P-1ZcPZg')
    btn6 = types.InlineKeyboardButton('Звук', url = 'https://uchitel.pro/задачи-на-звуковые-волны/')
    markup.add(btn6)
    markup.add(btn3)
    markup.add(btn4)
    markup.add(btn1)
    markup.add(btn2)
    markup.add(btn5)
    bot.send_message(message.chat.id, 'Вот задачи:', reply_markup=markup)

@bot.message_handler(func=lambda m: m.text == 'ОГЭ')
def on_click(message):
        markup = types.InlineKeyboardMarkup()
        btn1 = types.InlineKeyboardButton('Сайт ОГЭ по физике', url='https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://phys-oge.sdamgia.ru/&ved=2ahUKEwjD_KCd1fGRAxUnExAIHTPSFVYQFnoECA0QAQ&usg=AOvVaw3Vrg2IFz8yV5-zDhE-eURG')
        btn2 = types.InlineKeyboardButton('Сайт ОГЭ по математике ', url = 'https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://math-oge.sdamgia.ru/&ved=2ahUKEwjM_L2n1_GRAxUZJRAIHSmKIQUQFnoECCAQAQ&usg=AOvVaw3OoXed9Vtazu-828RiArXw')
        btn3 = types.InlineKeyboardButton('Сайт ОГЭ по русскому ', url = 'https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://rus-oge.sdamgia.ru/&ved=2ahUKEwiJlonF1_GRAxWZORAIHRF0K2wQFnoECBMQAQ&usg=AOvVaw2s-NSEa0-LlWhnsK6AATpd')
        btn4 = types.InlineKeyboardButton('Сайт ОГЭ по английскому ', url = 'https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://en-oge.sdamgia.ru/&ved=2ahUKEwi2zM_Y1_GRAxVmGRAIHc7CBV0QFnoECA4QAQ&usg=AOvVaw1QlnBckS8jahnVBXLkAR5p')
        markup.add(btn3)
        markup.add(btn4)
        markup.add(btn2)
        markup.add(btn1)
        bot.send_message(message.chat.id, 'ОГЭ', reply_markup=markup)

@bot.message_handler(func=lambda m: m.text == 'ИИ асистенты')
def on_click(message):
        markup = types.InlineKeyboardMarkup()
        btn1 = types.InlineKeyboardButton('DeepSeek', url='https://chat.deepseek.com')
        btn2 = types.InlineKeyboardButton('ChatGPT', url = 'https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://chatgpt.com/&ved=2ahUKEwj1_du61vGRAxV9IhAIHfi4G9kQFnoECAwQAQ&usg=AOvVaw29vbCnS_7PDD4xupasoOfg')
        markup.add(btn2)
        markup.add(btn1)
        bot.send_message(message.chat.id, 'ИИ', reply_markup=markup)



@bot.message_handler(commands=['task'])
def tasks(message):
    markup = types.InlineKeyboardMarkup()
    btn1 = types.InlineKeyboardButton('Тепловые явления', url='https://phys-oge.sdamgia.ru/test?theme=37')
    btn2 = types.InlineKeyboardButton('Электричество', url='https://sphksev.ru/wp-content/uploads/2020/04/P-10-Fizika.-Sila-toka.-Reshenie-zadach-na-30.04.2020.pdf')
    markup.add(btn1)
    markup.add(btn2)

    bot.reply_to(message, 'Задачи по физике:', reply_markup=markup)

@bot.message_handler(commands=['main'])
def about(message):
    bot.send_message(message.chat.id, "Здравствуйте Артем, я твой бот по физике...")

bot.polling(none_stop=True)
