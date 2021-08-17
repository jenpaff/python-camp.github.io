---
layout: default
---

Baustein 1 Meeting 2
====================

Listen und die for-schleife

* [1. Aufwärmübungen](#1-aufwärmübungen)
    *   [1.1. Ampelschaltung](#11-ampelschaltung)
    *   [1.2. Getränkeautomat](#12-getränkeautomat)
* [2. Listen](#2-listen)
    *   [Übungen zu Listen](#übungen-zu-listen)
* [3. for-Schleife](#3-for-schleife)
* [4. Übung: Labyrinth](#4-übung-labyrinth)
* [5. Weitere Übungen](#5-weitere-übungen)
    *   [5.1. for als while](#51-for-als-while)
    *   [5.2. Pyramiden bauen](#52-pyramiden-bauen)
    *   [5.3. Echte Pyramide](#53-echte-pyramide)
    *   [5.4. Zahlenmuster](#54-zahlenmuster)
    

1 Aufwärmübungen
----------------

### 1.1 Ampelschaltung

Deklariert euch eine Variable `farbe` mit dem Wert "rot" "grün" oder "gelb". Danach soll eine if - elif - else Struktur folgen, die Folgendes bewirkt: Wenn der Wert der Variable "rot" ist, soll er umgeändert werden in "grün". Wenn er "grün" ist soll er auf "gelb" umgeändert werden, und wenn er "gelb" ist soll er auf "rot" umgeändert werden (d.h die Variable soll überschrieben werden, so wie gestern bei der Gruß Variable). Gebt euch danach den Wert der Variable `farbe` zur Prüfung auf der Konsole aus. Hinweis: Genau wie bei Zahlen kann man Zeichenketten mit == vergleichen.

```python
farbe = 'gelb'
# ...
```


### 1.2 Getränkeautomat

Ihr sollt ein Programm für folgende Spezifikation schreiben: Ein Automat soll für eine Person mit bestimmten Alter automatisch das richtige Getränk ausgeben.

*   Personen unter 14 bekommen Orangensaft
*   Personen unter 18 bekommen Coca Cola
*   Personen unter 21 bekommen Bier
*   Personen die 21 und älter sind bekommen Whiskey

Definiert euch dazu eine Variable `alter` mit beliebigem Wert, und schreibt danach ein if-elif-else Befehl der das korrekte Getränk auf der Konsole ausgibt. Bonus: Es sollen die Getränke für alle Altersklassen aufgelistet werden. Schreibt eine while-Schleife die bis 25 zählt und in jedem Durchgang den Code aus Aufgabe 1 ausführt.

```python
alter = 10
# ...
```

### 1.3 Fibonacci

Intro: Die Fibonacci Sequence ist eine Zahlenfolge:
`0, 1, 1, 2, 3, 5, 8, 13, 21...`, wobei jede Zahl die Summe der vorherigen zwei Zahlen ergibt.
Beginnend bei `0` und `1`, die 3. Zahl in der Reihe ist `0` + `1` = `1`. 
Weiters, die 4. Zahl in der Reihe ist `1` + `1` = `2`, die 5. Zahl ergibt `1` + `2` = `3` usw.

Schreibe eine Schleife welche die Fibonacci Sequence bis 50 ausgibt. 

### 1.4 Celsius in Fahrenheit
Wir werden nun einen Rechner programmieren, welcher uns Celsius in Fahrenheit um wieder zurück umwandelt.

**Hier die Formeln**:

Fahrenheit in Celsius:
```
T(°C) = (T(°F) - 32) × 5/9
```

z.B.
```
T(°C) = (68°F - 32) × 5/9 = 20 °C
```

Celsius in Fahrenheit umrechnen:
```
T(°F) = T(°C) × 9/5 + 32 
```

z.B.
```
T(°F) = 20°C × 9/5 + 32 = 68 °F
```

**1.4.1 Aufgabe**:
- Deklariert eine Variable `temperature_value` um den Wert zu setzen welcher umgewandelt werden soll
- und eine Variable `temperature_unit`, welche angibt ob es sich bei dem Wert um die Einheit Celsius oder Fahrenheit handelt (z.B setzt `C` für Celsius 
und `F` für Fahrenheit) 
- wenn die `temperature_unit` als `C` angegeben wurde, dann wollen wir in Fahrenheit umrechnen
- wenn die `temperature_unit` als `F` angegeben wurde, dann wollen wir in Celsius umrechnen
- gib am Ende den konvertierten Wert aus 

### 1.4 EXTRA Celsius in Fahrenheit 

#### 1.4.2
- gib einen Text in der Konsole aus, wenn die Variable `temperature_unit` leer ist oder einen unbekannten Wert enthält

#### 1.4.3
- erweitere nun den Rechner um die Einheit `Kelvin`. Die Formel [findest du hier](https://www.rapidtables.com/convert/temperature/celsius-to-kelvin.html).



2 Listen
--------

Listen sind eine Sammlung von Elementen in fester Reihenfolge. Jedes Element einer Liste hat dabei einen festen _Index_, also eine Zahl, die beschreibt an welcher Stelle der Liste das Element steht.

In Programmiersprachen ist es üblich, dass eine solche Adressierung bei 0 beginnt.

`meine_liste = ["abc", "Stein", "Wasser", 1, 2]` ist zum Beispiel eine Liste der Länge 5. Die Zeichenkette "abc" ist das erste Element mit Index 0. "Stein" steht an zweiter Stelle mit Index 1. Weiss man zu einem Element den Entsprechenden Index, so kann man sich dieses Element aus der Liste holen in dem man in eckigen Klammern den Index hinter die Liste schreibt.

Listenelement kann alles Mögliche sein. Zahlen, Zeichenketten, Bool'sche Werte, sogar Listen können in Listen enthalten sein.

```python
meine_liste = ["abc", "Stein", "Wasser", 1, 2]
print(meine_liste[2]) #Wasser ist an Stelle 3, hat aber den Index 2.

# wie könnte man die Länge der Liste bestimmen?
```
```python
Wasser
```
Natürlich können Listen noch einiges mehr: Löschen, Hinzufügen, und Verändern von Elementen. Dafür gibt es wieder [ziemlich viel Funktionalität](https://docs.python.org/3/tutorial/datastructures.html) von der wir einen Teil kennen lernen werden.

```python
animals = ["Giraffe", "Affe", "Schnabeltier", "Oxolotl"]
# Zugriff:
animal = animals[2]
print("Element aus der Liste: " + animal)

# Verändern
animals[2] = "Großaugenmaki"

# Einfügen und Anhängen:
animals.insert(1, "Meerschweinchen")
animals.append("Pottwal")
print(animals)

# Löschen:
# ganze liste: del animals
# einzelnes Element nach index:
del animals[4]
print(animals)
# suchen und entfernen
animals.remove("Giraffe")
print(animals)
```
```python
Element aus der Liste: Schnabeltier
['Giraffe', 'Meerschweinchen', 'Affe', 'Großaugenmaki', 'Oxolotl', 'Pottwal']
['Giraffe', 'Meerschweinchen', 'Affe', 'Großaugenmaki', 'Pottwal']
['Meerschweinchen', 'Affe', 'Großaugenmaki', 'Pottwal']
```

### Übungen zu Listen:

#### Übung 2.1. 
Schreibe ein python Programm welches die Summe einer Liste ausgibt gegeben folgenden Inputs 

```python
input = [ 20, 1, 10, 3.5, 6.5, 9, 5, 5, 3, 7, 10]
```

#### Übung 2.2.
Schreibe ein python Programm welches die oben gegebene Liste in eine neue Liste `input_copy` kopiert

#### Extra Übungen
Um diese Übungen zu lösen, kann es sein, dass du [weitere Funktionalitäten](https://docs.python.org/3/tutorial/datastructures.html) 
der Liste nachschlagen musst. 

##### Übung 2.3.
Schreibe ein python Programm welches ausgibt ob eine Liste leer ist oder nicht. 

##### Übung 2.4.
Schreibe ein python Programm welches eine Liste rückwärts ausgibt. 

##### Übung 2.5.
Schreibe ein python Programm welches duplikate in einer Liste entfernt. 

### Weiteres zu Listen:

Und hier noch was Nützliches: Mit `split` kann man eine Zeichenkette anhand eines Trennzeichens aufteilen, und die "Splitter" in eine Liste stecken.

```python
satz = "The brown fox jumps over the lazy dog"
print(satz.split(" "))
```
```python
['The', 'brown', 'fox', 'jumps', 'over', 'the', 'lazy', 'dog']
```

3 for-Schleife
--------------

Es passiert auch häufig dass man eine Sequenz von Dingen der Reihe nach durchgehen muss, um mit jedem Element irgendwas zu machen. Mit der bereits bekannten `while` Schleife könnte man das natürlich machen, jedoch gibt es noch eine einfacherere Möglichkeit.

```python
users = ["Anton", "Bertha", "Caesar", "Detlef", "Emil"]
for name in users:
    # Name wird in jedem Schleifendurchlauf durch ein Listenelement ersetzt
    print(name + " ist super")
```

```python
Anton ist super
Bertha ist super
Caesar ist super
Detlef ist super
Emil ist super
```

Die `range` Funktion erlaubt es uns durch Zahlenfolgen zu iterieren. Dafür geben wir einen Anfangswert und eine Grenze der Zahlenfolge an. Optional können wir auch angeben wieviele Zahlen wir pro Schleifendurchlauf "springen".

```python
for i in range(1, 5):
    print(i)
```
```
1
2
3
4
```
```python
for i in range(1, 10, 2):
    print(i)
```
```
1
3
5
7
9
```


for-Schleifen können Grundsätzlich mit Allem arbeiten, was sich irgendwie nach einer festen Reihenfolge abzählen lässt. Zum Beispiel iterieren wir bei Zeichen/ketten/ durch die einzelnen Zeichen.
```python
string = "mallorca"
for letter in string:
    print(letter)
```
```
m
a
l
l
o
r
c
a
```


4 Übung: Labyrinth
------------------

check out [CodeCombat](https://codecombat.com/play/) for python gaming exercises

5 Weitere Übungen
-----------------

### 5.1 for als while

Versucht die selbe Funktionalität wie mit der for-Schleife oben mit einer while-Schleife zu erreichen.

### 5.2 Pyramiden bauen

Versucht, ein Python-Programm zu schreiben, welches die Pyramide
```
*
**
***
****
*****
******
*******
... etc.
```

ausgibt. Das Ganze soll in einer Schleife passieren, damit wir die höhe der Pyramide variieren können.

### 5.3 Echte Pyramide

Versucht, ein Python-Programm zu schreiben, welches eine "echte" Pyramide ausgibt:
```
*
**
***
****
*****
******
*******
******
*****
****
***
**
*
```


### 5.4 Zahlenmuster

Schreibt ein Programm welches euch das Muster
```python
1
22
333
4444
55555
666666
7777777
88888888
999999999
```

Auf der Konsole ausgibt. Zur Erinnerung: Mit `str(zahl_variable)` könnt ihr eine Zahl in eine Zeichenkette umwandeln. Mit `zeichenkette_variable * i` könnt ihr eine Zeichenkette i-mal wiederholen.