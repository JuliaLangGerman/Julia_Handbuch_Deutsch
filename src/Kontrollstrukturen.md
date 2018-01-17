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



