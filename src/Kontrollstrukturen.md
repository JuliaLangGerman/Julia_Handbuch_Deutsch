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

### if -- elseif -- else

Wir kommen gleich zu unserer ersten Kontrollstruktur die if-Verzweigung. Oft ist es so das wir in unseren Programmen Entscheidungen treffen müssen und anhand dieser Entscheidungen den Programmfluß entsprechend verzweigen müssen. Bis jetzt waren unsere Programme die wir direkt in die Shell getippt haben linear. Wir können jetzt zwar einfache Berechnung im interaktiven Modus durchführen.  

```julia
julia> r = 10;
julia> A = r^2 * pi
314.1592653589793
```

* ```pi``` ist eine built-in Konstante.  

Aber mit Hilfe von Kontrollstrukturen können wir wesentlich interessantere Programme schreiben. In den letzten beiden Kapiteln haben wir bereits die Vergleichsoperatoren kennen gelernt. Mit diesen können wir einfache Tests bauen die wir dann bei Entscheidungen verwenden können.  

* ``` x > 3 ``` wäre eine solche Bedingung die testet ob der Wert in ```x``` größer als 3 ist.  

Tippen Sie das folgende kleine Programm in eine Textdatei mit Namen ```verzweigung.jl```

```julia
x = 10  # wir benutzen hier eine fest zugewiesene Variable

if x > 3
  println("x > 3")
else
  println("x < 3 oder x = 3")
end
```
Anschließend starten Sie das Programm mit  

``` julia verzweigung.jl ```

Die Ausgabe sollte sein ```x > 3```  
Wenn Sie die Variable umgekehrt mal auf 1 setzen, dann wir die Ausgabe ```x < 3 oder x = 3``` lauten.  

Mit Hilfe der Zeile ```if BEDINGUNG``` legen wir fest was gestestet werden soll. Der darauf folgende Code bis zur Anweisung ```else``` wird ausgeführt wenn die Bedingung also unser Test ```true``` geliefert hat. Der Code von der else-Anweisung bis zur end-Anweisung wird ausgeführt wenn unser Test fehlschlug, also ```false``` lieferte. 

