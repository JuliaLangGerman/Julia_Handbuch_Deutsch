# Variablen

Oft kommt es vor das wir bestimmte Resultate unserer Berechnungen zwischen speichern möchten. Eine einfache Möglichkeit die wir in Julia haben, ist die Verwendung von Variablen und somit das vorübergehende Speichern im Arbeitsspeicher. Dabei führen wir eine Variable ein (deklarieren) und weisen ihr gleichzeitig einen Wert zu. Bevor eine Variable das erste mal genutzt werden kann, muss sie mit einem Wert initalisiert worden sein. 

```julia
julia> zahl = 15
15
julia> zahl
15
julia> zahl + 5
20
```

* ```=``` wird hier als Zuweisungoperator genutzt  

Das obigen Beispiele zeigen das wir mit Variablen genauso rechnen können wie mit normalen Zahlen bisher. Wir können einer Variable auch als Wert eine komplexe Zahl zuweisen und damit rechnen.

```julia
julia> z_1 = 2 + 3im
2 + 3im
julia> z_2 = 3 + 4im
3 + 4im
julia> z_1 + z_2
5 + 7im
```

### Interpolation

Die Interpolation von Strings haben wir bereits im Einführungsteil besprochen. Nun können wir dies auch noch um den Einsatz von Variablen ergänzen.

```julia
julia> name = "Christian"
"Christian"
julia> "Ich heiße $name"
"Ich heiße Christian"
```
Wie Sie im obigen Beispiel sehen können wir einer Variablen auch einen String zuweisen. Und mit ```$VARIABLEN_NAMEN``` können wir den Inhalt der Variable in einem String darstellen. 

### Die Umgebungsvariable ans

Eine Variable die bei unserer Interaktiven Sitzung immer mit dabei ist, ist die Variable ```ans```. In dieser wird das letzte Resultat gespeichert. 

```julia
julia> 2 + 3
5
julia> ans + 1
6
```

* Zu erst berechnen wir im interaktiven Modus 2+3 und bekommen natürlich 5 vom Interpreter zurückgegeben. 
* Als nächstes greifen wir auf ans zu und lassen uns ```ans + 1``` berechnen. Das Resultat ist 6, da ```ans``` das Resultat der letzten Berechnung enthält.

