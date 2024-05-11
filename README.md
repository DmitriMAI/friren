Документация к языку Friren. Написан на основе языка F#  
Данный язык основан на японском фильме   
"Встреча Фриры в ее бесповоротном пути"  
Вольный перевод от : 葬送のフリーレン  

Авторы проекта:
Овчинников Дмитрий М8О-306Б-21   | Документация   
Лохматов Никита М8О-306Б-21      | Добавление функциональности код 
Устинов Денис М8О-306Б-21        | Расширение файлов и работа над синтаксисом
Егор Аббдуллаев М8О-306Б-21      | Выбор названий функций и требования к их виду 
Егор Белоусов М8О-30*Б-21
# Комментарии 
Не все маги способны запомнить всю информацию.  
Важно оставлять заметки  
Обычный комментарий выглядит так (Однострочный):
```
/~ Some Comment ~/
```
# Переменные 
Можно использовать `=` либо `:` для объявления переменной  
`lt` - Link Trinket. Прикрепить волшебный брелок с магической силой внутри.   
(Теперь он будет весеть вместе с нами)
```
(lt NAME = VALUE)
(lt a = 4.0)
(lt b : 5.0)
(lt str = "str")
(lt boolean = true)
```
# Изменения переменных
Помочь с изменением способен `mut`  
Что означает мутацию состояния нашего брелка.
```
(mut a = 10)
```
# Поддержка базовой арифметики
Можно по разному объединять брелки  
Поддерживаются такие операции как :  `+`, `-`, `/`, `*`  
Пример
```
(
    cast (+ a b)
)
```
# Поддержка базовых булевый операций
Особый тип логических брелков.  
Для операций с ним нужны определенные инструменты.   
Доступны такие как: `&` и `|`
```
(
    /~  преобразует к false ~/
    cast (& true false)
)
```
# Поддержка операторов сравнения
Естественно некоторые брелки могут обладать большей силой.  
Необходимо сравнивать магическую силу.  
Есть варианты: `>`, `<`, `==`, `>=`, `<=`
```
cast(>= a b)
```
# Поддержка оператора if else  
Маг должен предусмотреть все варианты развития событий. В помощь ему магический разветвлитель
```
(
    if (> a b) =>
        (cast "a > b")
    else =>
        (cast "a < b")
)

/~  if может использоваться в одиночку ~/
(
    if (>= 1 1) =>
        (cast "true")
)
```
# Поддержка цикла for и while
Возможно мы хотим сделать четкий порядок обряда.  
И знаем, что придется повторять несколько действий снова и снова.  
Для таких случаев есть заклинения в помощь нам.  
Можно вызвать break с помощью `kill`    
А также continue с помощью `heal`  
```
(
    for i [0 .. 3] =>
        (cast i)
)

(
    while true =>
        ((cast "STOP!")
        kill)
)
```
# Cоставление сложных функций
Конечно же из собранных ингредиентов можно подготовить намного более сильное `spell` для следующего приключения.  
```
(
    spell printNum {num} =>
        (cast num)
)

/~ Можно использовать дальше в коде с помощью ~/
(printNum 100)
```
# Поддержка работы с файлами
Опытные маги всегда знают все на перед. Поэтому у них составлены магические свитки.  
Именно те маги которые ими пользовались остались жить дольше других.
```
/~ Получение выходных данных ~/
(cast (readGrim "./tests/input.txt") )

/~ Перенаправление вывода ~/
(writeGrim "./tests/output.txt" "Wow!")
```
