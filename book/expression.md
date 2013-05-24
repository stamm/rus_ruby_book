# Выражения

Выражение - это команда, возвращающая результат выполнения (обычно это объект) в место своего вызова. Выражения делятся на простые и сложные. Стандартные объекты и идентификаторы относятся к простым выражениям. Для выполнения вычислений из простых выражений создаются сложные выражения и предложения (которые являются одной из разновидностей сложных выражений). Части сложного выражения соединяются с помощью операторов и инструкций.

## Операторы

Простейший способ создания сложных выражений - объединение простых с помощью операторов. Операторы - это группа математических символов или знаков препинания. Составные части сложного выражения называют операндами. Операнды, в свою очередь, также относятся к выражениям и могут быть как простыми выражениями, так и сложными.

###### Классификация:

+ Унарные (У) 	- оперируют одним операндом;
+ Бинарные (Б) 	- оперируют двумя операндами;
+ Тернарные (Т) - оперируют тремя операндами.

Операторы также отличаются приоритетом и последовательностью вычисления операндов.

В сложных выражениях, содержащих несколько операторов, операнды будут вычисляться в порядке увеличения приоритета их операторов.

Если существует несколько операторов с одинаковым приоритетом (или только один оператор), то операнды вычисляются в том порядке, в котором были записаны. При R-последовательности это будет происходит справа налево, а при L-последовательности - слева направо.

Чтобы изменить процесс выполнения выражения, операнды, которые необходимо вычислить в первую очередь, отделяют двумя круглыми скобками.

\pagebreak

~~~~~ longtable
{ | * {5} { l |} }
Приор. & Лексема & Послед. & Тип & Название выражения
1 & ! ~ + & R & У Б У & логическое отрицание; \\* &&&& побитовое отрицание; \\* &&&& унарный плюс
2 & ** & R & Б & возведение в степень
3 & - & R & У & унарный минус
4 & \verb`* / %` & L & Б & произведение (копирование); деление; \\* &&&& остаток от деления (форматирование)
5 & + - & L & Б & сложение (объединение); \\* &&&& вычитание (удаление)
6 & \verb`<< >>` & L & Б & побитовый сдвиг влево (добавление) \\* &&&& побитовый сдвиг вправо
7 & \& & L & Б & побитовое И (пересечение множест)
8 & \verb`| ^` & L & Б & побитовое ИЛИ (объединение множеств); \\* &&&& побитовое исключающее ИЛИ
9 & < <= > >= & L & Б & отношение
10 & <=> ! = =~ & L & Б & сравнение; неравенство; поиск совпадений
10 & !~ == === & L & Б & отсутствие совпадений; равенство
11 & \&\& & L & Б & логическое И
12 & || & L & Б & логическое ИЛИ
13 & ?: & R & Т & логическое условие
14 & = & R & Б & присваивание
15 & not & R & У & логичекое отрицание
16 & and or & L & Б & логичекое И; логическое ИЛИ
~~~~~

\pagebreak

1. **!obj** (логическое отрицание)

  Используется для получения противоположного логического значения.

  ~~~~~ ruby
    !1 # -> false
    !nil # -> true
  ~~~~~

  **~ \\-, integer** (побитовое отрицание)

  Каждый бит числа изменяется на противоположный и дополняется до 1. В результате возвращается десятичное число, необходимое для дополнения. Аналогично выполнению выражения `-number-1`.

  ~~~~~ ruby
    ~1 # -> -2
    ~0b01 # -> -2
  ~~~~~

  **+ number** (унарный плюс)

  Возвращается число в десятичной системе счисления.  
  `+0b01 # -> 1`

2. __number**number__ (возведение в степень)

  Используется для возведения числа в степень. Первое операнд - основание степени, а второй - показатель.  
  `2**3 # -> 8`

3. **- number** (унарный минус)

  Используется для получения числа, противоположного по знаку.  
  `-0b01 # -> -1`

4. __number * number__ (произведение)

  Используется для перемножения двух чисел.  
  `1 * 2 # -> 2`

  __string * integer__ (копирование текста)

  Используется для копирования фрагмента текста заданное число раз.  
  `"R" * 3 # -> "RRR"`

  __array * integer__ (копирование массива)

  Используется для копирования фрагмента массива заданное число раз.  
  `[1, ?R] * 2 # -> [1, "R", 1, "R"]`

  __[*object]__ (извлечение элементов)

  Используется для извлечения элементов составного объекта.

  ~~~~~ ruby
    a = [1, 2, 3]
    [*a] # -> [1, 2, 3]
    [*a, 1] # -> [1, 2, 3, 1]
    b = { a: 1, b: 2 }
    [*b] # -> [ [:a, 1], [:b, 2] ]
    c = 1..4
    [*c] # -> [1, 2, 3, 4]
    [*1] # -> [1]
    [*nil] # -> [ ]
    [*?a] # -> ["a"]
  ~~~~~

  **number / number** (деление)

  Используется для деления двух чисел.  
  `-6 / 3 # -> -2`

  **number % number** (остаток от деления)

  Используется для целочисленного деления двух чисел. В результате возвращается остаток.
  ~~~~~ ruby
    7 % 3 # -> 1
    -7 % 3 # -> 2
    7 % -3 # -> -2
  ~~~~~

  **string % object** (форматирование)

  Используется для форматирования объекта согласно правилам, заданным [форматной строкой](appformat). В качестве объектов могут быть использованы числа, текст, индексный и ассоциативный массивы.

5. **number + number** (сложение)

  Используется для сложения двух чисел.  
  `1 + 3 # -> 4`

  **string + string** (объединение текста)

  Используется для объединения двух текстов.  
  `"Ruby" + ?! # -> "Ruby!"`

  **array + array** (объединение массивов)

  Используется для объединения элементов двух массивов.  
  `[1, 2] + [3, 4] # -> [1, 2, 3, 4]`

  **number - number** (вычитание)

  Используется для вычисления разности двух чисел.  
  `2 - 1 # -> 1`

  **array - array** (удаление элементов)

  Используется для удаления элементов из первого операнда.  
  `[1, 2, 2, ?R] - [2, ?1] # -> [1, "R"]`

6. **number << integer; number >> integer** (побитовый сдвиг)

  Сдвиг влево или вправо каждого бита на указанное количество разрядов.
  `1 << 2 # -> 4`

  **string << string** (добавление текста)

  Используется для добавления фрагмента в конец текста.

  Если вместо второго операнда передается целое число, то оно обрабатывается как кодовоя позиция символа.

  ~~~~~ ruby
    "Ruby" << ?! # -> "Ruby!"
    "Ruby" << 33 # -> "Ruby!"
  ~~~~~

  **array << object** (добавление элемента)

  Используется для добавления элемента в конец массива.  
  `[1] << 2 # -> [ 1, 2 ]`

7. **integer & integer** (побитовое И)

  Используется для сравнения битов.

  Если биты в одинаковых разрядах установлены в 1, то результирующий бит также устанавливается в 1.  
  `0b01 & 0b10 # -> 0`

  **array & array** (пересечение множеств)

  Используется для получения элементов, содержащихся в обоих массивах.  
  `[1, 2, 2, 3] & [2, 3] # -> [2, 3]`

8. **integer | integer** (побитовое ИЛИ)

  Используется для сравнения битов.

  Если любой из битов в одинаковых разрядах установлены в 1, то результирующий бит также устанавливается в 1.  
  `0b01 | 0b10 # -> 3`

  **array | array** (объединение множеств)

  Используется для получения элементов, содержащихся хотя бы в одном из массивов.  
  `[1, 2, 2, 3] | [2, 3] # -> [1, 2, 3]`

  **integer ^ \\-, integer** (побитовое исключающее ИЛИ)

  Используется для сравнения битов.

  Если один (и только один) из битов в одинаковых разрядах установлены в 1, то результирующий бит также устанавливается в 1.  
  `0b01 ^ 0b10 # -> 3`

9. **< <= >= >** (отношение)

  Проверка отношения двух объектов.

  Для чисел:

  ~~~~~ ruby
    1 <= 2 # -> true
    1 > 2 # -> false
  ~~~~~

  Для текста:

  При проверке текста последовательно проверяется каждый байт. Первый отрицательный результат станет результатом выполнения всего выражения.

  Каждая следующая буква алфавита считается больше, чем предшественница.

  Любая строчная буква считается больше, чем любая прописная буква.

  ~~~~~ ruby
    "а" < "б" # -> true
    "а" < "Б" # -> false
    "1" <= "2" # -> true
  ~~~~~

10. **object == object** (равенство)

  Проверка равенства двух объектов. Объекты считаются равными, если их значения и типы равны.

  ~~~~~ ruby
    1 == 1.0 # -> true
    1 == "1" # -> false
  ~~~~~

  **object != object** (неравенство)

  Проверка равенства двух объектов.

  ~~~~~ ruby
    1 != 1.0 # -> false
    1 != "1" # -> true
  ~~~~~

  **object === object** (идентичность)

  Аналогично проверке на равенство, кроме случаев, которые будут описаны отдельно (по умолчанию операнды должны ссылаться на один и тот же объект).

  ~~~~~ ruby
    1 === 1.0 # -> true
    1 === "1" # -> false
  ~~~~~

  **string =~\\-, regexp; regexp =~\\-, string** (поиск совпадений)

  Используется для поиска по тексту совпадений с [образцом](appregexp). В результате возвращается индекс символа, с которого начинается найденный фрагмент, или ссылка на nil, если совпадений не найдено.

  **string !~\\-, regexp; regexp !~\\-, string** (остутствие совпадений)

  Проверка отсутствия совпадений.

  **object <=> object** (сравнение)

  Сравнение двух объектов.

  ~~~~~ ruby
              < = >
    # ->	-1 0 1
  ~~~~~

  _-1_ если первый операнд меньше второго;  
  _0_ если операнды равны;  
  _1_ если первый операнд больше второго;  
  _nil_ если сравнение операндов невозможно (разные типы операндов).

  Сравнить можно два числа, текста, индексных массива (последовательно сравнивается каждый элемент).

  ~~~~~ ruby
    1 <=> 1.0 # -> 0
    1 <=> ?2 # -> nil
  ~~~~~

11. **expression && expression** (логическое И)

  Второй операнд вычисляется только при положительном результате вычисления первого операнда.

  ~~~~~ ruby
    4 && 2 - 1 # -> 1
    3 > 4 && 2 - 1 # -> false
  ~~~~~

12. **expression || expression** (логическое ИЛИ)

    Второй операнд вычисляется только при отрицательном результате вычисления первого операнда.

    ~~~~~ ruby
      4 || 2 - 1 # -> 4
      3 > 4 || 2 - 1 # -> 1
    ~~~~~

13. **expression ? expression : expression** (логическое условие)

  В зависимости от результата вычисления первого операнда вычисляется второй операнд (для истинных значений) или третий операнд (для ложных значений)

    ~~~~~ ruby
      1 > 2 ? true : false # -> false
      1 < 2 ? true : false # -> true
    ~~~~~

14. **identificator = object** (присваивание)

  Используется для [присваивания](appassign) значений идентификаторам.

  __**= *= /= %= += -= <<= >>= &&= &= ||= |= ~=__ (псевдооператоры)

  Псевдооператоры - это операторы, получившиеся в результате объединения с оператором присваивания.  
  `<1> op= <2>` аналогично `<1> = <1> op <2>`

15. **not object** (логическое отрицание)

  Аналогично `!object`, но с меньшим приоритетом.

16. **expression and expression** (логическое И)

  Аналогично `expression && expression`, но с меньшим приоритетом.

  **experssion or expression** (логическое ИЛИ)

  Аналогично `expression || expression`, но с меньшим приоритетом.

## Предложения

Предложения - это одна из разновидностей сложных выражений, создаваемая с помощью инструкций (поэтому количество возможных видов предложений строго ограничено). Каждое предложение начинается с инструкции, объявляющей тип предложения и заканчивается инструкцией end, объявляющей конец предложения. Между этими двумя инструкциями находится фрагмент кода, называемый телом предложения, ходом выполнения которого манипулирует предложение.

### Условное предложение

Условные предложения управляют ходом выполнения в зависимости от логического значения переданного условия. В результате выполнения предложения возвращается результат выполнения последнего выражения в его теле (или nil).

###### Синтаксис предложения:

Тело предложения выполняется при положительном результате вычисления условия.

~~~~~ ruby
  if условие
    тело_предложения
  end
~~~~~

Тело предложения должно быть отделено от условия либо переводом строки, либо точкой с запятой, либо инструкцией then.

###### Инструкция else:

Содержит фрагмент кода, который выполняется при отрицательном результате вычисления условия.

~~~~~ ruby
  ...
    тело_предложения
  else
    код
  end
~~~~~

При необходимости записать подряд инструкцию else и новое условное предложение используется инструкция elsif.

###### Краткий синтаксис:

`тело_предложения if условие`

Тело предложения либо должно находиться на одной строке с условием, либо быть ограничено инстуркциями begin и end, либо быть ограничено двумя круглыми скобками.

~~~~~ ruby
  begin
    тело_предложения
  end if условие
~~~~~

или

~~~~~ ruby
  ( тело_предложения
  ) if условие
~~~~~

Если вместо инструкции if использовать инструкцию unless, то тело предложения будет выполняться при отрицательном результате вычисления условия. Инструкция elsif в этом случае не используется.

### Разветвленное условие

Разветвленные условия похожи на условные предложения, но позволяют проверять сразу несколько условий. Условия проверяются последовательно. Обычно наиболее вероятные варианты записывают раньше остальных - это уменьшит время выполнения предложения. В результате выполнения предложения возвращается результат выполнения последнего выражения в его теле (или nil).

###### Синтаксис предложения:

Выполняется фрагмент кода с положительным результатом ввычисления условия.

~~~~~ ruby
  case
    when условие
      код
    when условие
      код
    ...
  end
~~~~~

Условие может состоять из нескольких выражений, разделенных запятыми. Любое из них может послужить причиной для выполнения кода.

###### Специальный синтаксис:

Проверяется равенство значения условия и указанных выражений (с помощью `===`).

~~~~~ ruby
  case условие
  when выражение
    код
  when выражение
    код
  ...
  end
~~~~~

В любой форме можно использовать инструкцию else.

### Цикл

Цикл - это предложение итеративного типа (заставляющее программу повторно выполнять некоторый фрагмент кода). Циклы используются в том случае, когда число итераций неизвестно заранее. В результате выполнения цикла возвращается ссылка на nil.

~~~~~ note
Цикл while не соотвествует слову "пока" в естественном языке. Условие цикла не проверяется непрерывно, а только до или после каждой итеарции.
~~~~~

###### Синтаксис предложения:

Тело предложения выполняется до тех пор пока результат вычисления условия истинен (условие проверяется до итерации).

~~~~~ ruby
  while условие
    тело_цикла
  end
~~~~~

Тело цикла должно быть отделено от условия либо переводом строки, либо точкой с запятой, либо инструкицей do.

###### Сокращенный синтаксис:

`тело_цикла while условие`

Тело цикла и условие обязательно должны находиться на одной строке кода. Если тело цикла ограничено инструкциями begin и end, то условие проверяется после итерации. Также тело цикла может быть ограничено двумя круглыми скобками.

~~~~~ ruby
  begin
    тело_цикла
  end while условие
~~~~~

или

~~~~~ ruby
  ( тело_цикла
  ) while условие
~~~~~

Если вместо инструкции while использовать инструкцию until, то тело цикла будет выполняться до тех пор пока результат вычиления условия ложен.

~~~~~ note
Использование инструкции until эквивалентно конструкции while not.

Для создания бесконечного цикла существует частный метод экземпляров из модуля Kernel - \verb`.loop { }`, который используется для бесконечного выполнения блока до возникновения исключения \verb`StopIteration` или вызова специальных инструкций. Данный метод эквивалентен конструкции while true.
~~~~~

### Перебор элементов

Перебор элементов - это предложение итеративного типа, выполняющее фрагмент кода для каждого элемента составного объекта.

~~~~~ ruby
  for параметр in объект
    тело_перебора
  end
~~~~~

Параметр в теле перебора ссылается на элементы составного объекта (может быть использовано несколько параметров, разделенных запятыми).

Для составного объекта должен существовать метод `.each`, который будет использоваться в ходе выполнения предложения.

Тело предложения должно быть отделено либо переводом строки, либо точкой с запятой, либо инструкцией do.

### Управление ходом выполнения

Ход выполнения предложения может быть изменен с помощью специальных инструкций в его теле. Необязательный код, передаваемый инструкции возвращается в результате выполнения предложения. Если код отсутствует, то возвращается ссылка на nil.

##### Инструкции:

`return [код]` - используется для завершения выполнения предложения и всех методов, в теле которых оно выполняется, продвигаясь вверх по областям видимости;

`break [код]` - используется для завершения выполнения предложения;

`next [код]` - используется для завершения текущей итерации цикла и начала следующей;

`redo` - используется для повторного выполнения текущей итерации. Проверка условия при этом не выполняется.

*****

## Триггеры

В качестве условия могут быть использованы триггеры. Триггер - это сложное выражение, составленное с помощью операторов `..` или `...`. Эти операторы имеют приоритет выполнения больше, чем у оператора условия и меньше, чем у оператора логического ИЛИ (примерно 12.5). В условии может использоваться только один триггер.

Как и обычные условия, триггеры имеют некоторое логическое значение. Его особенность в том, что оно может изменяться в зависимости от результатов предыдущих вычислений, т.е. триггер сохраняет состояние выполнения.

Обычно триггеры применяются вместе с регулярными выражениями для обработки текста между начальными и конечными шаблонами.

###### Синтаксис триггера:

`условие..условие`; `условие...условие`

Операнды триггера - это два условия, при проверке которых логическое значение триггера либо остается неизменным, либо изменяется на противоположное. Порядок проверки условий зависит от оператора, используемого для создания триггера.

Значение триггера ложно до тех пор пока ложно значение первого условия. После смены логического значения первого условия изменяется и логическое значение триггера. Оно будет сохраняться до тех пор пока логическое значение второго условия ложно. После смены логического значения второго условия, изменяется и логическое значение триггера и проверка условий начинается сначала.

###### Процесс выполнения триггера:

1. Если логическое значение триггера ложно, то проверяется первое условие. В зависимости от его логического значения устанавливает логическое значение триггера. После его возвращения для оператора `..` также проверяется второе условие.

2. Если логическое значение триггера истинно, то проверяется второе условие. Если логическое значение второго условия истинно, то логическое значение триггера меняется.

~~~~~ note
По смыслу триггеры довольно похожи на диапазоны. Они верны до тех пор пока существующее состояние выполнения находится от достижения первого условия и до достижения второго условия. Оператор `...` включает состояние достигнувшее второе условие, а оператор `..` - нет.
~~~~~