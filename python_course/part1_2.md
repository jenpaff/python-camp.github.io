---
layout: default
---

Baustein 1 Meeting 2
====================

Listen und die for-schleife

*   [1\. Aufwärmübungen](#1-aufwrmbungen)
    *   [1.1. Ampelschaltung](#11-ampelschaltung)
    *   [1.2. Getränkeautomat](#12-getrnkeautomat)
*   [2\. Listen](#2-listen)
*   [3\. for-Schleife](#3-for-schleife)
*   [4\. Übung: Labyrinth](#4-bung-labyrinth)
*   [5\. Weitere Übungen](#5-weitere-bungen)
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
    \# Name wird in jedem Schleifendurchlauf durch ein Listenelement ersetzt
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

Die bisher kennengelernten Sprachbausteine scheinen aktuell noch sehr abstrakt, und man mag sich fragen wozu man sie denn braucht. Wie ihr schnell beim Lösen von Aufgaben und dem Umsetzen von Projekten merken werdet, sind sie aber absolut essentiell und werden sehr oft gebraucht.

In dieser Aufgabe benutzen wir Listen und schleifen um ein Labyrinth zu erstellen, und dann einen Spielecharakter durch dieses Spielfeld zu bewegen.

Ladet euch den Quellcode für diese Übung bitte [hier](https://github.com/falcowinkler/falcowinkler.github.io/raw/master/resources/python-course/python_labyrinth.zip) herunter. Die Datei muss dann vollständig entpackt werden (Das ist wichtig, unter windows funktioniert es sonst nicht). Öffnet dann die Datei playground.py in dem Ordner. Wenn ihr das Programm startet, seht ihr eine Spielfigur die sich über ein (noch relativ leeres) Spielfeld bewegt.

*   Mit dem Befehl `set_size(breite, hoehe)` könnt ihr die Größe eures Spielfeldes festlegen.
*   Es gibt eine männliche und eine weibliche Spielfigur, die ihr mit der Funktion `waehle_spieler()` auswählen könnt.

Es gibt `steve` `amy` oder `default` zur Auswahl.

*   Nutzt den `block`\-Befehl um ein Labyrinth zu erstellen. Die Zahlen sind (x, y) Koordinaten,

und es gibt "Dreck", "Gras", "Wasser", "Ziel", und "Kohle".

*   Nutzt den `bewegung`\-Befehl, um euch durch das Labyrinth zu Bewegen (Erlaubte Parameter sind links, rechts, hoch, runter).

Falls ihr euch mit den Koordinaten nicht sicher seid, seht ihr hier eine Übersicht aller Koordinaten für ein 10 x 10 Labyrinth:

![grid.png](https://raw.githubusercontent.com/falcowinkler/falcowinkler.github.io/master/resources/python-course/grid.png)

Figure 1: Koordinatensystem

Wenn euch diese Übung Spass gemacht hat, schaut mal auf [CodeCombat](https://codecombat.com/play/) :)

5 Weitere Übungen
-----------------

### 5.1 for als while

Versucht die selbe Funktionalität wie mit der for-Schleife oben mit einer while-Schleife zu erreichen.

### 5.2 Pyramiden bauen

Versucht, ein Python-Programm zu schreiben, welches die Pyramide
```
\*
\*\*
\*\*\*
\*\*\*\*
\*\*\*\*\*
\*\*\*\*\*\*
\*\*\*\*\*\*\*
... etc.
```

ausgibt. Das Ganze soll in einer Schleife passieren, damit wir die höhe der Pyramide variieren können.

### 5.3 Echte Pyramide

Versucht, ein Python-Programm zu schreiben, welches eine "echte" Pyramide ausgibt:
```
\*
\*\*
\*\*\*
\*\*\*\*
\*\*\*\*\*
\*\*\*\*\*\*
\*\*\*\*\*\*\*
\*\*\*\*\*\*
\*\*\*\*\*
\*\*\*\*
\*\*\*
\*\*
\*
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