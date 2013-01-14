[appdatetime]()
# Форматирование времени

Форматная строка состоит из групп символов вида:
\\*`%[модификатор][размер][спецсимвол]`. 

Любой текст, не относящийся к спецсимволам или модификаторам переносится в результат без изменений. 

Размер влияет на количество символов в результате. Если размер меньше, чем необходимое количество символов, то он игнорируется интерпретатором.

##### Модификаторы:
**-** - ограничение размера игнорируется;
**_** - для выделения используются пробелы;
**0** - для выделения используются нули (по умолчанию);
**^** - результат в верхнем регистре;
**#** - изменяет регистр символов.
##### end

##### Год:
**%Y** - номер года с веком;  
```
  Time.local( 1990, 3, 31 ).strftime "Год: %Y" # -> "Год: 1990"
  Time.local( 1990, 3, 31 ).strftime "Год: %7Y" # -> "Год: 0001990"
  Time.local( 1990, 3, 31 ).strftime "Год: %-7Y" # -> "Год: 1990" 
  Time.local( 1990, 3, 31 ).strftime "Год: %_7Y" # -> "Год:    1990" 
  Time.local( 1990, 3, 31 ).strftime "Год: %07Y" # -> "Год: 0001990"
```
     
**%G** - номер года с веком. В качестве первого дня в году обрабатывается понедельник; 
\\`Time.local( 1990, 3, 31 ).strftime "Год: %G" # -> "Год: 1990"`
    
**%y** - остаток от деления номера года на 100 (от 00 до 99);  
\\`Time.local( 1990, 3, 31 ).strftime "Год: %y" # -> "Год: 90"`
    
**%g** - остаток от деления номера года на 100 (от 00 до 99). Первым днем года считается понедельник; 
\\`Time.local( 1990, 3, 31 ).strftime "Год: %g" # -> "Год: 90"`
    
**%C** - номер года, разделенный на 100 (20 в 2011);  
\\`Time.local( 1990, 3, 31 ).strftime "Век: %C" # -> "Век: 19"`
##### end

##### Месяц:
**%b (%h)** - аббревиатура названия месяца (три первые английские буквы);   
\\`Time.local( 1990, 3, 31 ).strftime "Месяц: %b" -> "Месяц: Mar"`    
  
**%B** - полное названию месяца;
```
  Time.local(1990, 3, 31).strftime "Месяц: %B" # -> "Месяц: March"
  Time.local(1990, 3, 31).strftime "Месяц: %^B" # -> "Месяц: MARCH"
  Time.local(1990, 3, 31).strftime "Месяц: %#B" # -> "Месяц: MARCH"
```
   
**%m** - номер месяца (от 01 до 12);  
\\`Time.local( 1990, 3, 31 ).strftime "Месяц: %m" -> "Месяц: 03"`
##### end

##### Неделя:
**%U** - номер недели (от 00 до 53). Первое воскресенье года считается началом первой недели;  
\\`Time.local( 1990, 3, 31 ).strftime "Неделя: %U" -> "Неделя: 12"`
   
**%W** - номер недели (от 00 до 53). Первый понедельник года считается началом первой недели;  
\\`Time.local( 1990, 3, 31 ).strftime "Неделя: %W" -> "Неделя: 13"` 
   
**%V** - номер недели (от 01 до 53) (номер недели в формате ISO 8601);  
\\`Time.local( 1990, 3, 31 ).strftime "Неделя: %V" -> "Неделя: 13"` 
##### end

##### День:
**%j** - день года (от 001 до 366);  
\\`Time.local( 1990, 3, 31 ).strftime "День: %j" # -> "День: 090"`
   
**%d** - день месяца;  
\\`Time.local( 1990, 3, 3 ).strftime "День: %d" # -> "День: 03"`
   
**%e** - день месяца;  
\\`Time.local( 1990, 3, 3 ).strftime "День: %e" # -> "День:  3"`
   
**%a** - аббревиатура дня недели (три первые английские буквы);  
\\`Time.local( 1990, 3, 31 ).strftime "День: %a" # -> "День: Sat"`
   
**%A** - полное название дня недели;  
\\`Time.local( 1990, 3, 31 ).strftime "День: %A" # -> "День: Saturday"`
   
**%u** - номер дня недели (от 1 до 7, понедельник - 1);  
\\`Time.local( 1990, 3, 31 ).strftime "День: %u" # -> "День: 6"`
   
**%w** - номер дня недели (от 0 до 6, воскресенье - 0);  
\\`Time.local( 1990, 3, 31 ).strftime "День: %w" # -> "День: 6"`
##### end

##### Час:
**%H** - час дня в 24 часовом формате (от 00 до 23);  
\\`Time.local( 1990, 3, 31 ).strftime "Час: %H" # -> "Час: 00"`    
   
**%k** - час дня в 24 часовом формате (от 0 до 23);  
\\`Time.local( 1990, 3, 31 ).strftime "Час: %k" # -> "Час:  0"`    
   
**%I** - час дня в 12 часовом формате (от 01 до 12);  
\\`Time.local( 1990, 3, 31 ).strftime "Час: %I" # -> "Час: 12"`    
   
**%l** - час дня в 12 часовом формате, с приставкой в виде знака пробела (от 0 до 12);  
\\`Time.local( 1990, 3, 31 ).strftime "Час: %l" # -> "Час: 12"`   
   
**%p** - индикатор меридиана ("AM" или "PM"); 
\\`Time.local( 1990, 3, 31 ).strftime "%I %p" # -> "12 AM"`    
   
**%P** - индикатор меридиана ("am" или "pm");  
\\`Time.local( 1990, 3, 31 ).strftime "%I %P" # -> "12 am"`   
##### end

##### Минуты и секунды:
**%M** - количество минут (от 00 до 59);  
\\`Time.local( 1990, 3, 31 ).strftime "мин: %M" # -> "мин: 00"`    
   
**%S** - количество секунд (от 00 до 60);  
\\`Time.local( 1990, 3, 31 ).strftime "сек: %S" # -> "сек: 00"`    
   
**%N** - дробная часть секунд.

+  _%3N_ - миллисекунды;
+  _%6N_ - микросекунды;
+  _%9N_ - наносекунды (по умолчанию);
+  _%12N_ - пикосекунды.
  
**%L** - количество миллисекунд (от 000 до 999); 
\\`Time.local( 1990, 3, 31 ).strftime "мс: %L" # -> "мс: 000"`    
   
**%s** - количество секунд, прошедших начиная с 1970-01-01 00:00:00 UTC;  
\\`Time.local( 1990, 3, 31 ).strftime "%s" # -> "638827200"`   
##### end
  
##### Форматы:
**%D** - форматная строке `"%m/%d/%y"`;
```
  Time.local( 1990, 3, 31 ).strftime "Дата: %D"
  # -> "Дата: 03/31/90"
```
     
**%F** - форматная строке `"%Y-%m-%d"` (время в формате ISO 8601); 
```
  Time.local( 1990, 3, 31 ).strftime "Дата: %F"
  # -> "Дата: 1990-03-31"
```   
   
**%v** - форматная строке `"%e-%b-%Y"` (время в формате VMS); 
```
  Time.local( 1990, 3, 31 ).strftime "Дата: %v"
  # -> "Дата: 31-MAR-1990"
``` 
   
**%c** - формат системы;
```
  Time.local( 1990, 3, 31 ).strftime "Система: %c"
  # -> "Система: Sat Mar 31 00:00:00 1990"
```
   
**%r** - форматная строке `"%I:%M:%S %p"!; 
\\`Time.local( 1990, 3, 31 ).strftime "%r" # -> "12:00:00 AM"`
   
**%R** - форматная строке `"%H:%M"!; 
\\`Time.local( 1990, 3, 31 ).strftime "%R" # -> "00:00"`
   
**%T** - форматная строке `"%H:%M:%S"!; 
\\`Time.local( 1990, 3, 31 ).strftime "%T" # -> "00:00:00"`
##### end

##### Форматирование:
**%n** - перевод строки;
```
  Time.local( 1990, 3, 31 ).strftime "%D %n %F %n %c"
  # -> "03/31/90 \n 1990-03-31 \n Sat Mar 31 00:00:00 1990"
```   
   
**%t** - отступ;
```
  Time.local( 1990, 3, 31 ).strftime "%D %t %F %t %c"
  # -> "03/31/90 \t 1990-03-31 \t Sat Mar 31 00:00:00 1990"
```  
##### end

##### Остальное:
**%x** - только дата; 
\\`Time.local( 1990, 3, 31 ).strftime "%x" # -> "03/31/90"`    
   
**%X** - только время; 
\\`Time.local( 1990, 3, 31 ).strftime "%X" # -> "00:00:00"`    
   
**%z** - смещение часового пояса относительно UTC; 
\\`Time.local( 1990, 3, 31 ).strftime "%z" # -> "+0400"`

+ _%:z_ - часы и минуты разделяются с помощью двоеточия;
\\`Time.local( 1990, 3, 31 ).strftime "%:z" # -> "+04:00"`

+ _%::z_ - часы, минуты и секунды разделяются с помощью двоеточия;
\\`Time.local( 1990, 3, 31 ).strftime "%::z" # -> "+04:00:00"`
  
**%Z** - название временной зоны; 
\\`Time.local( 1990, 3, 31 ).strftime "%Z" # -> "MSD"`
   
**%%** - знак процента.
##### end