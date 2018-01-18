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
* ```println``` ist eine Funktion mit der wir einen String auf der Konsole ausgegeben können. Wenn wir unsere Programme in Textdateien unterbringen, dann verwenden wir für die Ausgabe println. 

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

### Ternary Operator

Wenn Sie aus einer der Programmiersprachen C, C++, Java, C# kommen dann kennen Sie bestimmt den ternary operator.
Die Syntax sieht wie folgt aus:  

``` BEDINGUNG ? WERT1 : WET2 ```

Dieses Konstrukt kann einer Variable zugewiesen werden, aber auch einer Funktion übergeben werden. Es funktioniert wie folgt, wenn die BEDINGUNG ```true``` liefert dann wird WERT1 zurückgegeben (z.B. an die Variable übergeben) ansonsten wir der WERT2 übergeben. Bei den "Werten" kann es sich auch um Strings oder sonstige Objekte handeln. 

## Schleifen

Oft kommt es beim Programmieren vor das wir bestimmte Anweisungen (Sequenzen) wiederholen müssen. Die Zahl der Wiederholungen kann direkt bekannt sein, kann aber auch von entsprechenden Bedingungen abhängen. In Julia gibt es zwei zentrale Schleifen Arten.

### while - Schleife

Die erste ist die sogenannte while-Schleife. Diese Schleife wiederholt einen Codeblock solange wie die Schleifenbedingung ```true``` ist. 

```julia
counter = 1

while counter <= 10
  println(counter)
  counter += 1
end
```

Das obige Programme zählt von 1 bis 10. Die Schleifenbedingung ist hier ```counter <= 10```. Solange diese Bedingung true ist, wiederholen wir den Codeblock der zur Schleife gehört. Damit wir irgendwann aus der Schleife herauskommen, müssen wir die Variable ```counter``` bei jedem Durchgang um Eins erhöhen. Das machen wir mit dem Update-Operator ```+=``` 

Es empfiehlt sich auch hier das Sie den Code einfach mal nach tippen und ihn dann ausführen. 

### Endlosschleife

Mit der while-Schleife muss man etwas aufpassen. Ein Fehler der oft auch noch Profis passiert ist, das sie im Schleifenkörper - dem Codeblock der Schleife - keine Veränderung der Schleifenbedingung vorsehen. Dann wir die while-Schleife niemals verlassen. Gehen Sie einfach mal hin und kommentieren Sie die Zeile ```counter += 1``` aus. Setzen Sie einfach vor die Zeile ein ```#```. Dann übersetzen Sie das Programm erneut. Allerdings müssen Sie dann das Programm gewaltsam beeenden! 

Ihr Programm wird dann solange wie Sie es laufen lassen 1 ausgeben. Sie sollten immer einen Fluchtweg parat haben. Also dafür sorgen das die Schleife irgendwann wieder verlassen wird. 

### break und continue

Mit Hilfe des Statement ```break``` verlassen Sie die Schleife direkt, egal ob es sich um eine while-Schleife oder eine for-Schleife handelt. Mit der ```continue``` Anweisung kehrt das Programm zum Schleifenkopf zurück. Das bedeutet es wird eine neue Iteration gestartet. 

```julia
counter = 1

while true
  if counter == 11
    break           # unser Fluchtweg
  end
  println(counter)
  counter += 1
end
```

Oben das gleiche Programme, welches von 1 bis 10 zählt. Nun aber mit einem eingebauten Fluchtweg ```break``` in Kombination mit einer ```if``` Verzweigung. Ich empfehle auch hier, tippen Sie das Programm nach und testen Sie es! 

```julia
counter = 1
loop = true

while loop
  if counter == 11
    loop = false    # ganz wichtig da sonst endlos!
    continue      
  end
  println(counter)
  counter += 1
end
```

Oben das gleiche Programm welches auch wieder von 1 bis 10 zählt. Diesmal nutzen wir ```continue```. Der zentrale Unterschied ist das wir diesmal einen kleinen Schalter eingebaut haben nämlich die boolische Variable ```loop```, mit ihr können wir die Schleife abschalten und somit verlassen. Das wir diese auch zum richtigen Zeitpunkt verlassen haben wir ```continue``` in Kombination mit der ```if``` Verzweigung verwendet. Auch hier gilt wieder ausprobieren. 

### for-Schleife

Die for-Schleife (manchmal auch Zählschleife genannt) können Sie immer dann einsetzen, wenn Sie genau wissen wie oft Anweisungen wiederholt werden müssen. Um bei dem einfachen Beispiel von oben zu bleiben, bei dem wir einfach von 1 bis 10 zählen. Können wir dies wesentlich eleganter mit einer for-Schleife machen. 

```julia
for counter = 1 : 10
  println(counter)
end
```

Schon ein gewaltiger Unterschied! Wir kommen ohne unnötige Variablen und unötige Zuweisungen aus. Die Wahl der richtigen Kontrollstruktur hat einen großen Einfluss auf die lesbarkeit des Codes. Hier nochmal die Syntax:  

```julia
for LAUFVARIABLE = START : END
  # mach was
end
```

#### for-each

Die for-Schleife können wir noch in einer Sonderform betrachten nämlich der for-each Schleife. Gerade wenn wir über eine Datenstruktur laufen wollen, kann es vernünftiger sein eine for-each Schleife zu nutzen. Entsprechende Datenstrukturen wie das Array werden wir noch näher behandeln. Im moment begnügen wir uns mit Strings. Ein String ist auch eine Datenstruktur die verschiedene Zeichen enthält und Operationen darauf zulässt!

```julia
str = "hallo welt"

for ch in str
  println(ch)
end
```

Das obige Programm gibt auf jeder Zeile ein Zeichen des Strings ```str``` aus.  
Syntax 

```julia
for LAUFVARIABLE in DATENSTRUKTUR
  # mach was
end
```

Die Laufvariable nimmt hier bei jedem Durchlauf ein neues Element aus der Datenstruktur an. Im obigen Beispiel eben ein Zeichen. 

## Ausnahme-Behandlung

Dieses Thema gehört auch in die Kategorie Kontrollstrukturen, da es entsprechende Kontrollstrukturen gibt um sogenannte Ausnahmen zu behandeln. Was ist  aber eine Ausnahme? Für gewöhnlich verhält sich der Programmfluss ihrer Programme so, das wenn es zu einem unerwarteten Problem kommt, das Programm einfach mit einigen (für den Anwender meist unverständlichen) Fehlermeldungen terminiert. 

Machen Sie einfach mal im interaktiven Modus folgendes Experiment.

```julia
julia> sqrt(-1)
```
Wer mathematisch etwas fast im Sattel sitzt der weis das man von einer negativen Zahl nicht die Quadratwurzel ziehen kann. Oder um genauer zu sein für die reellen Zahlen gibt es für die Quadratwurzel einer negativen Zahl kein Resultat.  

Wenn Sie das obige Experiment gemacht haben werden Sie wahrscheibnlich folgende Fehlermeldung erhalten haben

```
ERROR: DomainError:
sqrt will only return a complex result if called with a complex argument. Try sqrt(complex(x)).
 in sqrt at ./math.jl:146
```

Wenn so etwas währen des Programmflusses auftritt, dann spricht man von einer **Ausnahme**, also ein Fehler der zur Laufzeit auftritt. 

Stellen Sie sich vor Sie möchten ein Programm für die Berechnung der Quadratwurzel schreiben.

**User Story 1:** Der Benutzer kann eine Zahl eingeben für die dann die Quadratwurzel berechnet wird.  
**User Story 2:** Gibt der Benutzer eine negative Zahl ein, so soll er darüber infomiert werden das er ein komplexes          Ergebnis bekommt und zu dem wird das komplexe Resultat ausgegeben.

Man könnte die Eingabe negativer Zahlen einfach mittels ```if``` Abfrage realisieren. Da wir aber in diesem Abschnitt Exception Handling behandeln, werden wir eine neue Kontrollstruktur einführen. 

```julia
try 
  # mach was
  # hier kann es knallen!
catch e
  # behandlung der Ausnahme
end
```

Zwischen ```try``` und ```catch e``` darf irgendwelcher Code stehen, in dem Sie damit rechnen das es zu einem Problem kommen kann. Wenn dann ein Fehler auftritt wird von diesem Codeblock ```try ... catch e``` in den darunter liegenden gesprungen. 
Es wird dann der Code zwischen ```catch e``` und ```end``` ausgeführt. 

```julia
print("Zahl? ") # einfaches prompt
eingabe = parse(Float64, readline()) # einlesen über readline()

try
    println("Das Resultat ist $(sqrt(eingabe))") # berechnung + ausgabe
catch e
    println("Negative Eingabe: Sie erhalten ein komplexes Ergebnis!") # warnhinweis
    println("Resultat ist $(sqrt(complex(eingabe)))") # berechnung + ausgabe
end
```

* ```readline``` benutzen wir zum einlesen eines Strings(!) über dien Konsole.   
* ```parse```  benutzen wir um den eingelesen String in den Datentype Float64 zur parsen. Dadurch können wir dann die Eingabe als eine Fließkommazahl betrachten und sie der Funktion ```sqrt``` übergeben.

Die Variable ```e``` die wir beim ```catch``` Zweig immer sehen, enthält zusätzliche Fehlerinformationen. Mit Hilfe von ```println``` können Sie den Inhalt von ```e``` einfach ausgeben.  

---

[Zurück zum Inhaltsverzeichnis](../README.md)
