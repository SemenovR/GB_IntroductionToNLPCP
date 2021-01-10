### Итоговый проект курса "Введение в обработку естественного языка"

Стек:
1. ML: FastText, CountVectorizer, TfidfVectorizer, MorphAnalyzer, dialogflow, LogisticRegression, annoy
2. API: telegram

Данные: разговорная часть модели обучалась на вопросах-ответах mail.ru, продуктовая часть с сайта youla.ru (раздел одежды).

Задача: реализовать чат-бот.

Реализация:<br>
Чат-бот реализован на базе API Telegram. <br>
При поступлении текстового запроса модель сначала определяет является ли запрос на тему "поговорить" или "поиск продукта" с помощью MorphAnalyzer, CountVectorizer и LogisticRegression. Если запрос продуктовый, то используя FastText, TfidfVectorizer и annoy определяются 3 наиболее подходящие продукта, которые затем отображаются в чате. Если же запрос разговорный, то используя те же FastText, TfidfVectorizer и annoy определяется наиболее подходящий ответ. Если найденный ответ, для первого и второго случая, слабо соответствует запросу (определяется дистанция через annoy), то запрос передаётся в dialogflow. Если и dialogflow не сможет вернуть результат, то чат-бот отвечает 'Не понимаю.'.

Файл cproject_train.ipynb содержит обучение моделей.<br>
Файл cproject_bot.ipynb содержит готовую модель чат-бота.