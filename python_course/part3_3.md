---
layout: default
---

Baustein 3 Meeting 1

* [1\. Wiederholung und Warmup](#1-wiederholung-und-warmup)
    * [1.1. Übung: Wetterdaten auswerten](#11-bung-wetterdaten-auswerten)
* [2\. Fortgeschrittene Sprachkonstrukte](#2-fortgeschrittene-sprachkonstrukte)
    * [2.1. Übung](#21-bung)
* [3\. Python - Standardbibliothek](#3-python---standardbibliothek)
    * [3.1. Übung](#31-bung)
    * [3.2. Wiederholung](#32-wiederholung)

Baustein 3 Meeting 1
====================

1 Wiederholung und Warmup
-------------------------

### 1.1 Übung: Wetterdaten auswerten

Eure Aufgabe ist es, Wetterdaten (gegeben als `str`) in einem bestimmten Format, in Python auszuwerten. Schreibt eine Funktion `parse_rain_data(data)`, welche einen String im folgenden Format entgegennimmt `Rome:Jan 81.2,Feb 63.2,Mar 70.3,Apr 55.7,May 53.0,Jun 36.4,Jul 17.5,Aug 27.5,Sep 60.9,Oct 117.7,Nov 111.0,Dec 97.9` Zuerst kommt die Stadt, gefolgt von einem Doppelpunkt Dann mit Komma getrennt die Regenfall-Daten für die einzelnen Monate. Ein Monat hat immer drei Buchstaben Die Funktion soll die Stadt als string, sowie die Regenfälle als Liste von Zahlen zurückgeben.

#### 1.1.1 Tipps

* Die string Funktion `.split(trener)` ist hier sehr nützlich. Probiert mal `.split(":")` und `.split(",")` auf dem Beispiel-String aufzurufen.
* Die Ersten vier Zahlen (der Monat) lassen sich aus einem String mit `str[4:]` entfernen. Zum Beispiel: `"Apr 55.7"[4:]`
* Gegeben eine Zeichenkette `"55.7"` könnt ihr diese mit `float(55.7)` in eine Zahl umwandeln
* Vielleicht ist es einfacher, eine Funktion zu extrahieren die einzelne Zellen (`"Apr 55.7"` zum Beispiel) in eine Zahl umwandelt. Dann muss man doch eigentlich nur noch die Funktion auf die gesamte Liste _anwenden_ (denkt an die letzte Übung gestern). Das müsst ihr aber nicht machen.

```python
def anwenden(funktion, liste):
neue_liste = \[\]
for element in liste:
neues_element = funktion(element)
neue_liste.append(neues_element)
return neue_liste
```

* Wenn ihr hinter dem `return` in einer Funktion mehrere Werte mit Komma getrennt schreibt, könnt ihr mehrere Werte zurückgeben.

#### 1.1.2 Beispiel:

```
data="Rome:Jan 81.2,Feb 63.2,Mar 70.3,Apr 55.7,May 53.0,Jun 36.4,Jul 17.5,Aug 27.5,Sep 60.9,Oct 117.7,Nov 111.0,Dec 97.9"
parse_rain_data(data) # Rome, [81.2, 63.2, 70.3, 55.7, 53.0, 36.4, 17.5, 27.5, 60.9, 117.7, 111.0, 97.9]
```

Jetzt wollen wir uns den durchschnittlichen Regenfall im Jahr pro Stadt anschauen.

Dazu schreiben wir eine Funktion `city_average_rainfalls(data)`, welche mehrere Wetterdaten mit `\n` (Zeilenumbruch) auswertet. Sie gibt ein Wörterbuch mit der Stadt als Schlüssel, und dem durchschnittlichen Regenfall als Wert. Beispiel:

```
data = """Rome:Jan 81.2,Feb 63.2,Mar 70.3,Apr 55.7,May 53.0,Jun 36.4,Jul 17.5,Aug 27.5,Sep 60.9,Oct 117.7,Nov 111.0,Dec 97.9
London:Jan 48.0,Feb 38.9,Mar 39.9,Apr 42.2,May 47.3,Jun 52.1,Jul 59.5,Aug 57.2,Sep 55.4,Oct 62.0,Nov 59.0,Dec 52.9
Paris:Jan 182.3,Feb 120.6,Mar 158.1,Apr 204.9,May 323.1,Jun 300.5,Jul 236.8,Aug 192.9,Sep 66.3,Oct 63.3,Nov 83.2,Dec 154.7
NY:Jan 108.7,Feb 101.8,Mar 131.9,Apr 93.5,May 98.8,Jun 93.6,Jul 102.2,Aug 131.8,Sep 92.0,Oct 82.3,Nov 107.8,Dec 94.2"""
print(city\_average\_rainfalls(data)) \# {'Rome': 66.02499999999999, 'London': 51.199999999999996, 'Paris': 173.89166666666665, 'NY': 103.21666666666665}
```

([referenz](https://www.codewars.com/kata/56a32dd6e4f4748cc3000006/train/python))

2 Fortgeschrittene Sprachkonstrukte
-----------------------------------

So etwas wie die Funktion `anwenden` braucht man ziemlich häufig: Eine Funktion auf eine Liste (oder eine andere Datenstruktur) anwenden. Tatsächlich gibt es so etwas in python schon:

```python
print([x + 2 for x in [1, 2, 3, 7, 0, -1]])
print([name.upper() for name in ["hans", "gretel", "ruffi", "guenter"]])
```

```
[3, 4, 5, 9, 2, 1]
['HANS', 'GRETEL', 'RUFFI', 'GUENTER']
```

Diese Schreibweise nennt sich _list comprehension_. Mit der selben Schreibweise können wir auch _filtern_.

```python
print([x * 2 for x in [42, 73, 19, 11, 1, 5] if x % 2 == 0])
print([name.upper() for name in ["hans", "gretel", "ruffi", "guenter"] if name.startswith("g")])
```

```
[84]
['GRETEL', 'GUENTER']
```

### 2.1 Übung

Gegeben ist eine Klasse `Bewerber` :

```python
class Bewerber:
def __init__(self, name, gehaltsstufe):
self.name = name
self.gehaltsstufe = gehaltsstufe
```

Schreibe einen _list comprehension_ Ausdruck, der die Namen der Bewerber als Liste ergibt.

* Nur Bewerber mit einer Gehaltsstufe `<=2` sollen darin Enthalten sein.
* Namen sollen immer mit einem Grossbuchstaben beginnen und danach mit Kleinbuchstaben geschrieben sein (`title`).

```python
bewerber = [Bewerber("günni", 1), Bewerber("EdelTraut", 2), Bewerber("MAGGIE", 99)]
# Günni, Edeltraut
```

3 Python - Standardbibliothek
-----------------------------

Bibliotheken kann man sich als Packete von Python code vorstellen, die im python code den ihr entwickelt eingebunden werden können. Dazu verwendet man den `import` Befehl.

```python
import collections
```

Man kann dann Klassen und Funktionen in diesen Packeten mit Punktnotation aufrufen.

```python
import collections
my_dict = collections.defaultdict(lambda: 0)
```

Diese Punktnotation kann man sich auch sparen:

```python
from collections import defaultdict
my_dict = defaultdict(lambda: 0)
```

Was ist also jetzt die Bibliothek `collections`? Sie enthält praktische Funktionen im Umgang mit Datenstrukturen. `defaultdict` ist zum Beispiel ein Wörterbuch, welches immer einen Wert liefert, auch wenn der Schlüssel nicht vorhanden ist.

```python
from collections import defaultdict
my_dict = defaultdict(lambda: 0)
my_dict["Rome"] = 42
my_dict["London"] = 33
print(my_dict["Rome"])
print(my_dict["Lissabon"]) # Kein Key Error, sondern 0
```

```
42
0
```

Eine weitere praktische Klasse aus dem Packet `collections` ist `Counter`. Mit ihr können wir die Vorkommen von Elementen zählen.

```python
from collections import Counter
print(Counter("Bananarama"))
print(Counter([5, 1, 2, 6, 12, 1, 5, 2]))
```

```
Counter({'a': 5, 'n': 2, 'B': 1, 'r': 1, 'm': 1})
Counter({5: 2, 1: 2, 2: 2, 6: 1, 12: 1})
```

Wie könnte man jetzt die Wörter in einem Text zählen?

### 3.1 Übung

Schreibt eine Funktion `most_occurring_word(filename)` die einen Dateinahmnen entgegennimmt, und dann die 10 häufigsten Wörter im Text (sortiert nach Anzahl der Vorkommen) ausgibt. Wir nehmnen vereinfacht an, dass keine Sonderzeichen im Text vorkommen.

Tipps:

* Mit `mein_counter.items()` bekommt ihr eine Liste von (Wort, Vorkommen) paaren. Diese könnt ihr dann sortieren, wenn ihr als `key` eine Funktion angebt, die die Vorkommen (das Zweite Element) aus dem Paar extrahiert.
* `"string.split()` ohne Argumente aufgerufen, nimmt als Trennzeichen alle _whitespace_ characters (Also Zeilenumbruch, Leerzeichen, Tabulator).

Andere Python-Dateien können wir auch wie Bibliotheken einbinden. Zur Demonstration wollen wir einmal die gerade geschriebene Funktion aus einer Seperaten Datei abrufen.

### 3.2 Wiederholung

`time`, `random` und `math` aus Kurs 1.