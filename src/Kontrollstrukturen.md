# Kontrollstrukturen

### Einsatz von Dateien

Bis jetzt haben wir im interaktiven Modus von Julia gearbeitet. Da unsere Programme jetzt aber immer länger und komplexer
werden, gehen wir dazu über diese in Textdateien abzuspeichern und sie dann dem Interpreter zugänglich zu machen. 
Sie benötigen dafür nur einen Texteditor ihrer Wahl und müssen die Textdateien mit der Endung **.jl** abspeichern.  

Um dem Interpreter die Textdatei zugänglich zu machen müssen Sie in den Konsole einfach nur schreiben:   

```bash
$ julia myProgram.jl
```
Der Julia-Interpreter lädt dann die Textdatei und übersetzt sie. 

## if -- elseif -- else

Wir kommen gleich zu unserer ersten Kontrollstruktur die if-Verzweigung. Oft ist es so das wir in unseren Programmen Entscheidungen treffen müssen und anhand dieser Entscheidungen den Programmfluß entsprechend verzweigen müssen. Bis jetzt waren unsere Programme die wir direkt in die Shell getippt haben linear. Wir können jetzt zwar einfache Berechnung im interaktiven Modus durchführen.  

```julia
julia> r = 10;
julia> A = r^2 * pi
314.1592653589793
```

* ```pi``` ist eine built-in Konstante.  

Aber mit Hilfe von Kontrollstrukturen können wir wesentlich interessantere Programme schreiben. In den letzten beiden Kapiteln haben wir bereits die Vergleichsoperatoren kennen gelernt. Mit diesen können wir einfache Tests bauen die wir dann bei Entscheidungen verwenden können.  

* ``` x > 3 ``` wäre eine solche Bedingung die testet ob der Wert in ```x``` größer als 3 ist.  


### if-else

Tippen Sie das folgende kleine Programm in eine Textdatei mit Namen ```verzweigung.jl```

```julia
x = 10  # wir benutzen hier eine fest zugewiesene Variable

if x > 3
  println("x > 3")
else
  println("x < 3 oder x = 3")
end
```

* Mit ```#``` beginnen wir einen Kommentar der über eine Zeile geht. Dieser Text wird vom Interpreter ignoriert.  

Anschließend starten Sie das Programm mit  

``` julia verzweigung.jl ```

Die Ausgabe sollte sein ```x > 3```  
Wenn Sie die Variable umgekehrt mal auf 1 setzen, dann wir die Ausgabe ```x < 3 oder x = 3``` lauten.  

Mit Hilfe der Zeile ```if BEDINGUNG``` legen wir fest was gestestet werden soll. Der darauf folgende Code bis zur Anweisung ```else``` wird ausgeführt wenn die Bedingung also unser Test ```true``` geliefert hat. Der Code von der else-Anweisung bis zur end-Anweisung wird ausgeführt wenn unser Test fehlschlug, also ```false``` lieferte. 

### elseif

Wir sind nun in der Lage einfache Verzweigungen zu bauen. Unser obiger Test welche Bedingung nun für die Variable x zutrifft könnte man aber wesentlich gezielter schreiben. Denn die Feststellung ```x < 3 oder x = 3``` ist nicht sehr Aussagekräftig.  

Ändern Sie den Code folgender Maßen ab.  


```julia
x = 10  # Wir benutzen hier eine fest zugewiesene Variable

if x > 3
  println("x > 3")
elseif x < 3  # 
  println("x < 3")
else 
  println("x = 3")
end
```

* Wir eine ```elseif``` Anweisung eingebaut. Damit können wir einen weiteren Test durchführen. Beachten Sie das der Programmfluss von oben nach unten läuft. Das bedeutet wenn der Test an der Stelle ```if x > 3``` fehlschlägt, dann geht es
an der Stelle ```elseif``` weiter. Wenn dieser Test auch fehl schlägt dann gehen wir in den else-Block.

Spielen Sie auch hier ruhig etwas mit dem Programm herum und ändern Sie die Variablenzuweisung. 

### Unterschiede zu MATLAB, C/C++ und Anderen

In Sprachen wie MATLAB aber auch C/C++ ist man gewöhnt das man bei den Kontrollstrukturen wann immer eine Bedinung verlangt wird auch einen numerischen Wert platzieren kann. Wenn dieser Wert ungleich 0 ist wird er als true interpretiert ansonsten zu false interpretiert. In Julia aber auch in Java muss der Wert eines Ausdrucks stets boolisch sein, das heißt also einen Wahrheitswert liefern. 

```c
if (1) 
{
  // mach was
}
```

Die obige Verzweigung würde in der Programmiersprache C funktionieren und der Codeteil ``` // mach was ``` würde ausgeführt werden. In Julia dagegen:  

```julia
if 1 
  # mach was
end
```

Bekommen Sie vom Interpreter auf die Finger geklopft!

## Codeblöcke

Im obigen Abschnitt habe ich von Blöcken gesprochen. Man bezeichnet den Teil zwischen ```if``` und dem nächsten ```elseif``` oder ```else``` als einen Codeblock. Diese Blöcke werden in unserem Fall ausgeführt, wenn eine bestimmte Bedingung gilt. Zum Beispiel x > 3 ist oder x = 3 ist usw.

### Compound Expressions (Sequenz)

Eine ganz einfache Kontrollstruktur in der Informatik ist die Sequenz. Dies ist eine aneinander Reihung von Anweisungen. 
Wir können uns diese Sequenz auch als einen Codeblock vorstellen.  

```julia
begin
  x = 5;
  y = 7;
  println(x+y)
end
```
Alles was zwischen ```begin``` und ```end``` steht umfasst einen Codeblock. In Julia können wir mit diesen Codeblöcken aber wesentlich mehr machen.

```julia
# Zuweisung an eine Variable
resultat = begin
              x = 5;
              y = 7;
              x+y
            end
 println(resultat)
```
Wir können diese Blöcke auch eine Variablen zuweisen. Jetzt könnten Sie fragen wie soll das gehen? Nun Julia ist auch **funktional** das bedeutet das Resultat der zuletzt ausgeführten Operation (in unserem Fall ```x+y```) wird von unsere Sequenze zurückgegeben. Dieses Resultat wird dann an die Variable übergeben. Das bedeutet die Sequenze in Julia ```begin end``` ist ein Ausdruck der einen Wert zurück gibt. 

## Ternary Operator

Wenn Sie aus einer der Programmiersprachen C, C++, Java, C# kommen dann kennen Sie bestimmt den ternary operator.
Die Syntax sieht wie folgt aus:  

``` BEDINGUNG ? WERT1 : WET2 ```

Dieses Konstrukt kann einer Variable zugewiesen werden, aber auch einer Funktion übergeben werden. Es funktioniert wie folgt, wenn die BEDINGUNG ```true``` liefert dann wird WERT1 zurückgegeben (z.B. an die Variable übergeben) ansonsten wir der WERT2 übergeben. Bei den "Werten" kann es sich auch um Strings oder sonstige Objekte handeln. 

---

[Zurück zum Inhaltsverzeichnis](../README.md)
