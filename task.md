# **Вариант 6: исполнитель кода в браузере**

Представляет из себя простую web форму с 2 полями для ввода и кнопкой launch.
В первое поле ввода мы вводим код файла на python (обязательное поле), во второе поле ввода - stdin (поле опциональное)

После нажатия кнопки Launch начинается исполнение кода на стороне сервера. После окончания работы программы - stdout и stderr отображаются на нашей странице

Требования:
1)	выполнение программы должно происходить внутри docker контейнера
2)	в целях обеспечения безопасности мы должны запретить импорт модуля os, а также работу built-in функции open (опционально: запускать программу с такими правами, чтобы прав на работу с файлами у неё не было), exec и eval
3)	Должна быть возможность выполнения нескольких программ одновременно
4)	Интерфейс должен выглядеть более или менее приятно
5)	(*) ... а также иметь подсветку синтаксиса python
6)	Программа должна выполняться с таймаутом, задаваемом в конфигурационном файле сервера
7)	(*) Должна иметься возможность выставить timeout на выполнение программы, который не превышает таймаут из предыдущего пункта
8)	(*) у программы должна быть возможность создавать файлы, контент которых будет выведен пользователю, а сами файлы - удалены
9)	(*) дополнительные security проверки, которые не дают выполняться коду как ниже в примере будут БОЛЬШИМ плюсом
```
>>> code = "(lambda  x: x).__globals__.['builtins']['open'].__doc__"[:100]"
>>> print(eval(code, {}, {})
```