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
