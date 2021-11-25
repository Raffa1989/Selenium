import string  # импортируем модуль string потмоу что я ленивое хуйло и не хочу писать каждую английскую букву
# берём из string метод string.ascii_lowercase который вернёт "abcdefghijklmnopqrstuvwxyz"

file_name = input('File name: ')
with open(file_name, 'r', encoding='utf-8') as f:  # без комментариев https://pavel-karateev.gitbook.io/intermediate-python/sintaksis/context_managers
    zalupa = f.read()

# форматирование текста
zalupa = zalupa.lower()  # приводим весь текст к нижнему регистру так как текст сейчас это одна строка
zalupa = zalupa.replace('.', '')  # удаляем все точки функцией replace, заменяя точку ничем
zalupa = zalupa.replace(',', '')  # аналогично 6й строке
zalupa = zalupa.split()  # разделяем всю строку на отдельные слова, создав список функцией split
unique_words = set(zalupa)  # получаем уникальные слова, по которым будем итерироваться. Зачем? Надо
# конец форматирования


words = {}  # пустой список для потому что
for word in unique_words:  # проходимя циклом по всей уникальной залупе
    if len(word) > 3:  # слова, что имеют размер менее трех символов идут нахуй
        words[word] = zalupa.count(word)  # добавляем в словарь слово в качестве ключа и значением количество вхождений в списке zalupa
frequent_word = max(words, key=words.get)  # находим ключ по максимальномуего значению

words_list = [i for i in words if i[0] in string.ascii_lowercase]  # создаём список слов, начинающихся с английской буквы

longest_word = max(words_list, key=len)  # находим ключ по максимальномуего значению
print(frequent_word, longest_word)  # печатаем всю эту залупу
