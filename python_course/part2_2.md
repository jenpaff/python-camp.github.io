---
layout: default
---

Baustein 2 Meeting 2
====================

*   [1\. Dateien lesen und schreiben](#sec-1)
*   [2\. Übungen (Dateien)](#sec-2)
    *   [2.1. Dateien zusammenführen](#sec-2-1)
    *   [2.2. Wörter zählen](#sec-2-2)
*   [3\. Bibliotheken](#sec-3)
    *   [3.1. math](#sec-3-1)
    *   [3.2. time](#sec-3-2)
    *   [3.3. random](#sec-3-3)


Thema der heutigen Einheit sind hauptsächlich _Bibliotheken_. Bibliotheken sind im Kern von anderen Entwicklern bereitgestellte Funktionen und Klassen, die es uns erlauben, vorgefertigte Implementierungen zu nutzen und so umfangreiche Programme zu schreiben.

1 Dateien lesen und schreiben
-----------------------------

Bisher wurden alle Daten in unseren Programmen gelöscht, sobald das Programm beendet wurde. (Nur die Konsolenausgabe bleibt noch eine Weile da). Um Daten zu persistieren oder einfach Informationen aus einer Datei zu lesen, gibt es in Python eine Built-In Funktion `open`. Diese Funktion liefert eine Referenz auf eure Datei. Ihr könnt eine Datei im Modus w für 'write', a für 'append', und r für read öffnen. Es ist dabei wichtig, eine Datei nach Verwendung immer mit `close` zu schließen. Sonst kann es zu Problemen kommen wenn die Datei erneut geöffnet wird, und es werden Ressourcen verschwendet. Die Methode write fügt keinen Zeilenumbruch ein, wie ihr das von `print` gewohnt seid. Ein Zeilenumbruch muss mit der sog. Escape-Sequenz `\n` manuell hinzugefügt werden.

```python
# Schreiben in eine Datei

file_object = open("kundendaten.txt", "w")
file_object.write("Herr Meier, 42, Angestellt\\nHerr Müller, 32, Selbstständig")
file_object.close()

# Lesen einer Datei
file_object = open("kundendaten.txt", "r") # read-mode
# Zeile für zeile in einer Schleife
for line in file_object:
print(line)

# Die Referenz sollte geschlossen werden, damit andere Programme
# Wissen, dass wir die Datei nicht mehr brauchen
file_object.close()
```

```
Herr Meier, 42, Angestellt

Herr Müller, 32, Selbstständig
```

Dieser Code erzeugt genau [diese Datei.](https://falcowinkler.github.io/org/kundendaten.txt) Die Sache mit dem close könnt ihr euch mit dem `with` Schlüsselwort einfacher machen. Dieses definiert einen Codeblock, nach dessen Ausführung die geöffnete Datei immer geschlossen wird.

```python
with open("kundendaten.txt", "r") as file_object, open("ausgabe.txt", "w") as out:
for line in file_object:
print(line)
out.write("!!!" + line)
# close nicht benötigt
```

```
Herr Meier, 42, Angestellt

Herr Müller, 32, Selbstständig
```

2 Übungen (Dateien)
-------------------

### 2.1 Dateien zusammenführen

Wir wollen ein kleines Programm schreiben, welches alle Zeilen aus einer Datei A an eine andere Datei B anhängt. Dazu müsst ihr Folgendes, der Reihe nach, tun:

*   Datei A lesend öffnen (`open("meine_datei_A.txt", "r")`)
*   Datei B im Anhänge-Modus öffnen (`open("meine_datei_B.txt", "a")`)
*   Datei A Zeile für Zeile durchlaufen, und jede Zeile mit `write` in Datei b schreiben.

([Lösung](https://falcowinkler.github.io/resources/python-course/kurs_2_2_files1.py))

### 2.2 Wörter zählen

*   Schreibt ein Programm welches die Wörter in einer Datei zählt.

([Lösung](https://falcowinkler.github.io/resources/python-course/kurs_2_2_files2.py))

3 Bibliotheken
--------------

Funktionen und Klassen können in eine sogenannte Bibliothek "verpackt" und so wiederverwendbar gemacht werden. Andere Entwickler können diese Bibliotheken dann über den Befehl import verwenden. In Python sind schon einige Bibliotheken vorinstalliert: Sie Enthalten Funktionalität die häufig gebraucht wird, wie zum Beispiel das Rechnen mit Datumswerten und Zeiten, Mathematische Funktionen, Interaktion mit dem Betriebssystem und so weiter. Auch die bisher kennengelerten Built-in Funtionen wie str oder input zählen zu dieser standard - Bibliothek. Eine Übersicht gibt es hier: [https://docs.python.org/3/library/](https://docs.python.org/3/library/) Wir werden heute beispielhaft die Bibliotheken math, random und time kennenlernen.

### 3.1 math

In dieser Bibliothek findet man alle wichtige mathematische Funktionen. Die braucht man in Computerprogrammen vielleicht häufiger als man denken mag. Durch den Befehl import math können wir in der Syntax math.<funktion> auf alle Funktionen zugreifen. Will man sich das math. vorneweg sparen, kann man auch from math import \* schreiben.

```python
import math

print(math.pi)

from math import *

print(pi)

radius = 20
umfang = radius * 2 * pi
print(umfang)

print(log(1)) # Logarithmus und Exponentialfunktion
print(log(exp(7)))
print(gcd(4, 8)) # Größter gemeinsamer teiler

print(sqrt(2)) # Wurzel
print(sqrt(9))
```

```
3.141592653589793
3.141592653589793
125.66370614359172
0.0
7.0
4
1.4142135623730951
3.0
```

Die Funktionen in dieser Bibliothek benötigt man wenn man z.B. eine bestimmte Formel explizit ausrechnen muss. Bzgl. der Funktion Sinus gibt es den folgenden Zusammenhang.

```latex
\\begin{align} sin(\\frac{\\pi} {4}) = \\frac{\\sqrt(2)}{2} \\end{align}
```

Angenommen wir wollen Prüfen ob diese Gleicheit stimmt.

```python
from math import *
print(cos(pi)) # cosinus
print(sin(pi)) # sinus (eigentlich 0, Ungenauigkeit in der Berechnung)

print(sin(pi/4))
print(sqrt(2)/2)

print(sin(pi/4) == sqrt(2)/2)
print(isclose(sin(pi/4), sqrt(2)/2))
```

```
-1.0
1.2246467991473532e-16
0.7071067811865475
0.7071067811865476
False
True
```


Warum ergibt der direkte Vergleich mit `==` `False`? Der Grund liegt wieder in der Ungenauigkeit von Fließkommazahlen in Computern. Ihr erinnert euch eventell:

```
print(0.1 + 0.2)
```

```
0.30000000000000004
```

Die `math` Bibliothek achtet nicht auf solche Rundungen. Mit `math.isclose(a,b)` kann man aber zum Beispiel zwei Zahlen auf Gleichheit prüfen, auch wenn sie ein bisschen verschieden sind.

### 3.2 time

Diese Bibliothek kann für das Umgehen mit Zeitintervallen, oder einfach dafür das aktuelle Jahr, den aktuellen Tag usw. rauszufinden (mit `gmttime`). Man kann auch die Zeit messen, die euer Programm zur Ausführung braucht.

```python
import time

print ("Sekunden seit 1970 : " + str(time.time()))

#Zeitattribute:
zeitattribute = time.gmtime()
print(zeitattribute.tm_wday) # Wochentag 1, = dienstag, 2 2= mittwoch
print(zeitattribute)
# So kann man zum beispiel die Zeit messen
vorher = time.time()
sum = 0
for i in range(1000000):
sum += -1 * i

nachher = time.time()
print(nachher-vorher)

# Mit strptime kann man aus einem String ein Datum machen
birthday = time.strptime("19.08.95", "%d.%m.%y")
print(birthday.tm_wday)
```

```
Sekunden seit 1970 : 1595074860.415776
5
time.struct\_time(tm\_year=2020, tm\_mon=7, tm\_mday=18, tm\_hour=12, tm\_min=21, tm\_sec=0, tm\_wday=5, tm\_yday=200, tm\_isdst=0)
0.10863518714904785
5
```

#### 3.2.1 Übung

Schreibt eine Funktion `get_weekday` die ein Datum im üblichen europäischen Format (z.B. "01.02.2013") (das Format dafür ist `"%d.%m.%Y"`, grosses `Y`) entgegennimmt, und den Wochentag dafür als Zahl zurückgibt. Wenn noch Zeit ist, erweitert dann die Funktion damit sie den Wochentag als Zeichenkette zurückgibt ("Mittwoch" zum Beispiel) Wer schon früher fertig ist: Schreibt eine Funktion, die euch die Anzahl an Tagen von jetzt bis zu einem gegebenen Datum liefert.

```python
import time

def get_weekday(date_as_string):
...
return ...
```


([Lösung](https://falcowinkler.github.io/resources/python-course/kurs_2_2_time.py))

### 3.3 random

Mit `random` kann man zufällige Zahlen erzeugen. Außerdem gibt es noch einige Funktionen für Listen, die ein zufälliges Element zurückgeben oder die Elemente zufällig neu anordnen.

```python
import random

print(random.randint(0,8)) # Zufällige Zahl im Bereich 0 bis 8
print(random.random()) # Zufällige Kommazahl im bereich 0 - 1
print(random.random() * 10 + 20) # Zufällige Kommazahl im bereich 20-30

# Welches kleid heute? ;)
print(random.choice(["Das rote", "Das blaue", "Das grüne"]))

sortiert = [1, 2, 3, 4, 5, 6]
random.shuffle(sortiert)
print(sortiert)
```

```
3
0.9038792075990757
24.915161351963732
Das blaue
[3, 5, 2, 1, 4, 6]
```

#### 3.3.1 Übung

Wir schreiben eine Funktion, die einen Satz als parameter bekommt, und die Reihenfolge der Wörter zufällig verändert. Der veränderte Satz wird als String zurückgegeben.

Zur Erinnerung:

*   `string.split("trennzeichen")` spaltet einen String in Teile
*   `"trennzeichen".join(liste)` fügt eine Liste aus strings wieder zusammen, mit dem Trennzeichen dazwischen.

```python
def randomize_sentence(sentence):
...
```