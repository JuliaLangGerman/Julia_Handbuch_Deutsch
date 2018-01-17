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

Wir kommen gleich zu unserer ersten Kontrollstruktur. 


