## examples
1. [Basic (url) rules](http://gshumihin.github.io/examples/filterrules/01_basic_rules.html#)
 * [Blocking](http://gshumihin.github.io/examples/filterrules/01_basic_rules.html#)
 * [Exceptions](http://gshumihin.github.io/examples/filterrules/01_2_Exceptions.html#)
 * [Options](#options)
    * $image, $stylesheet, $xmlhttprequest
    * $empty
    * $popup
    * $mp4
  * $replace rules
  * RegExp rules
2. [Elemhide](http://gshumihin.github.io/examples/filterrules/02_Elemhide.html#)
3. CSS injections
4. JS rules
5. HTML filtering rules

#### Options

Соответствие началу/концу адреса

Обычно Adguard обрабатывает каждое правило так, как если бы оно имело символ обобщения * в начале и в конце. Например, нет разницы между правилами ad и *ad*. Обычно это не является проблемой, но иногда вы можете захотеть, чтобы ваше правило соответствовало в начале или в конце адресов. Например, вы можете захотеть заблокировать весь Flash, но если вы добавите правило swf, адрес http://example.ru/swf/index.html также будет заблокирован.

Решение проблемы: добавьте к правилу символ |, чтобы показать, что конец адреса находится в этой точке. Например, правило swf| будет блокировать http://example.ru/annoyingflash.swf , но не http://example.ru/swf/index.html. А правило |http://baddomain.example/ будет блокировать http://baddomain.example/banner.gif , но не http://gooddomain.example/analyze?http://baddomain.example.

Иногда нужно заблокировать не только http://domain.ru, но и http://www.domain.ru, или http://adv.domain.ru. Это может быть достигнуто добавлением двух символов | в начало правила, который соответствует началу доменного имени: ||example.com/banner.gif будет блокировать все эти адреса, но не тронет http://gooddomain.ru/banner.gif или http://gooddomain.ru/analyze?http://domain.ru/banner.gif.

Разделительные символы

Часто вам нужно будет применить в правиле любой разделительный символ. Например, вы можете написать правило, которое блокирует http://domain.com/ , но не http://domain.com.ua/. Здесь символ ^ может быть использован как указатель для одного разделительного символа: http://domain.com^.

Разделитель — это любой символ кроме букв, цифр или одного из следующих символов: — . %, а также это может быть конец адреса. В следующем примере все разделители показаны красным:

http://domain.com/foo.bar?a=12&b=%D1%82%D0%B5%D1%81%D1%82.
Этот адрес может быть блокирован правилом ^domain.com^ или ^%D1%82%D0%B5%D1%81%D1%82^ или ^foo.bar^.

Комментарии

Любое правило, начинающееся с восклицательного знака содержит комментарий. Оно отображается в списке правил серым цветом. Adguard будет игнорировать это правило при блокировании, так что можете спокойно писать там всё, что хотите. Вы можете, например, расположить комментарий выше реального правила, чтобы описать для чего оно нужно.

Расширенные возможности

Возможности, описанные в этом разделе, обычно используются опытными пользователями. Они расширяют возможности «Общих правил», но для их применения необходимо иметь начальное представление о работе браузера.

Вы можете изменить поведение «общего правила», используя дополнительные параметры. Список этих параметров располагается в конце правила за знаком доллара $ и разделяется запятыми. Например:

||domain.ru$match-case,third-party.
Здесь ||domain.ru - это само правило, а match-case и third-party - его параметры.
