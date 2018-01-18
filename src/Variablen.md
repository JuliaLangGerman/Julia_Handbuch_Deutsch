# Variablen

Oft kommt es vor das wir bestimmte Resultate unserer Berechnungen zwischen speichern möchten. Eine einfache Möglichkeit die wir in Julia haben, ist die Verwendung von Variablen und somit das vorübergehende Speichern im Arbeitsspeicher. Dabei führen wir eine Variable ein (deklarieren) und weisen ihr gleichzeitig einen Wert zu. Bevor eine Variable das erste mal genutzt werden kann, muss sie mit einem Wert initalisiert worden sein. 

### Deklaration und Initalisierung

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

### Update-Operatoren

Stellen Sie sich vor Sie wollen den Inhalt einer Variable um 1 erhöhen. Gehen wir davon aus wir haben eine Variable ```counter``` die mit 0 initalisiert ist und möchten in jedem Schritt den Wert um Eins erhöhen. Wir könnten zum Beispiel schreiben:

```julia 
counter = counter + 1
```

Beachten Sie das ```=``` der Zuweisungsoperator ist. Die obige Zeile wird dann vom Interpreter gelesen als, hole den Wert von ```counter``` addiere 1 dazu und speichere das Resultat wieder in der Variable ```counter```.

```julia
julia> counter = 0
0
julia> counter = counter +1
1
julia> counter
1
```

Das gleiche könnten Sie auch für alle anderen Operatoren schreiben. Zum Beispiel ```counter = counter / 5 ```  
Aber wir können das ganze mit Hilfe der Update-Operatoren kürzer und ausdrucksstärker schreiben.  

|Update-Operator | Bedeutung |
|----------------|-----------|
|x += y | x = x + y|
|x -= y | x = x - y |
|x *= y | x = x * y|
|x /= y | x = x / y |
|x %= y | x = x % y |
|x ^= y | x = x^y |

### Ein paar Konventionen

Es gibt ein paar [Konventionen](https://docs.julialang.org/en/stable/manual/variables/#Stylistic-Conventions-1) für die Benennung von Variablen. 

* Variablennamen sollten in Kleibuchstaben geschrieben sein. Siehe Beispiele oben.
* Worttrennungen sollte mit Unterstrichen _ realisiert werden. Zum Beispiel ```frame_counter```

### Ausgabe unterdrücken mit ;

Ähnlich wie in MATLAB können Sie im interaktiven Modus von Julia die Ausgabe der einzelnen Variablen unterdrücken.

```julia
julia> zahl = 5
5
```

Im obigen Beispiel wird nach dem bestätigen mit Enter der Wert der Variable nochmal ausgegeben. Um dies zu verhindern setzt man ein Semicolon nach der Variablenzuweisung.

```julia
julia> zahl = 5;

```

---

[Zurück zum Inhaltsverzeichnis](../README.md#inhaltsverzeichnis)
