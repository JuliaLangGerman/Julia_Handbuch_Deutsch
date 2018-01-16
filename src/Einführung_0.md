# Einführung in Julia

Es gibt drei zentrale Möglichkeiten Julia zu verwenden, entweder interaktiv (sowie man es zum Beispiel von MATLAB kennt), als Interpretersprache, oder als Compilersprache. 

Mit diesem Kommando

```bash
$ julia
```
starten Sie den interaktiven Modus. Dieser Modus eignet sich sehr gut gerade in der Einarbeitungsphase, aber auch um schnelle Berechnungen durchführen zu können. Wenn Sie Julia erlernen möchten ist es zu empfehlen, das Sie einfach ein bisschen damit rum spielen. 

Julia kennt wie jeder andere höhere Programmiersprache verschiedene Datentypen und deren mögliche Werte.

```julia
julia> 3
3
julia> 3.14
3.14
julia> 'c'
'c': ASCII/Unicode U+0063 (category Ll: Letter, lowercase)
julia> "hello world"
"hello world"
```

Oben haben wir bereits vier grundlegende Typen kennen gerlent. 

* Integer
* Float
* Char
* String

Die einzelnen Typen können Sie sich mit Hilfe der built-in Funktion **typeof** ausgeben lassen.

```julia
julia> typeof(3)
Int64
julia> typeof(3.14)
Float64
julia> typeof('c')
Char
julia> typeof("hello world")
String
```
Mit diesen Elementen können wir auch arbeiten also Operationen auf sie anwenden. 

```julia
julia> 3 + 3
6
julia> 7 - 2
5
julia> 3 * 2
6
julia> 5 / 2
2.5
julia> div(5,2)
2
julia> 5 % 2
1
julia> 2^3
8
```

Oben sehen Sie die verschiedenen mathematischen **Funktionen** in Julia. ```div```ist die ganzzahlige Division. ```%``` ist der Modulo Operator/Funktion. Tatsächlich handelt es sich bei diesen Operatoren um Funktionen im Sinne der funktionalen Programmierung! 

Beispiele

```julia
julia> + (2,3)
5
julia> %(5,2)
1
julia> ^(2,3)
8
```

Einen weiteren Datentype den wir kennen gelernt haben war String. Auf Strings können Sie auch Operationen anwenden.

```julia
julia> "haus"[1]
'h': ASCII/Unicode U+0068 (category Ll: Letter, lowercase)
julia> "hello world"[end]
'd': ASCII/Unicode U+0064 (category Ll: Letter, lowercase)
julia> "hello world"[1:5]
"hello"
```
So wie Sie es von anderen Programmiersprachen auch gewöhnt sind, können Sie auch mittels des Index-Operators **[]** auf die einzelnen Elemente eines Strings zugreifen. **Wichtig: Die Indexierung beginnt in Julia bei 1**   
Auch das sogenannte **Slicing** ist möglich. Wir können uns also bestimmte Teile unseres Strings heraus picken, wie Sie es im letzten Beispiel oben sehen, können wir aus dem String ```"hello world"``` das ```"hello"``` herausschneiden.

Funktionen für Strings

```julia 
julia> length("hello")
5
julia> in('h',"hello")
true
julia> in('c',"hello")
false
julia> string("hello ","world")
"hello world"

```
* Die Funktion ```length``` liefert die Länge des Strings.   
* Die Funktion ```in``` überprüft das Vorkommen eines bestimmten Zeichen in dem String. Diese Funktion wird uns auch später bei der Behandlung von Arrays wiederbegenen.  
* Die Funktion ```string``` können wir benutzen um Strings zu konkatenieren, also um Strings zusammenzufügen.  


Darüberhinaus haben wir einen neuen Datentype bzw. dessen Werte kennen gelernt nämlich den Datentype ```Bool``` dieser Datentype kennt nur zwei Werte nämlich ```true``` und ```false```. Diese Werte benötigen wir insbesondere bei den Kontrollstrukturen. Wir können nämlich mit Hilfe von true und false auf Ja/Nein Fragen antworten, was gerade bei Entscheidungen wichtig ist. 
