---
layout: default
---

Baustein 1 Meeting 4
====================

*   [1. Lösungen zu den letzten Aufgaben](#1-lsungen-zu-den-letzten-aufgaben)
    *   [1.1. Funktionen](#11-funktionen)
    *   [1.2. Number guessing game](#12-number-guessing-game)
*   [2. Mengen](#2-mengen)
    *   [2.1. Übung: gemeinsame Buchstaben](#21-bung-gemeinsame-buchstaben)
*   [3. Objektorientierte Programmierung](#3-objektorientierte-programmierung)
    *   [3.1. Klassen und Objekte](#31-klassen-und-objekte)
    *   [3.2. Übung: Objektorientiertes Bankkonto](#32-bung-objektorientiertes-bankkonto)
    *   [3.3. Übung (fortgeschritten): Piraterie](#33-bung-fortgeschritten-piraterie)
*   [4. Weiterführend: Python lernen](#4-weiterfhrend-python-lernen)
    *   [4.1. CodeCombat](#41-codecombat)
    *   [4.2. Coding - Katas](#42-coding---katas)
    *   [4.3. Online - Kurse](#43-online---kurse)
    *   [4.4. Eigene Projekte](#44-eigene-projekte)
    

1 Lösungen zu den letzten Aufgaben
----------------------------------

(Alle Lösungen sind nur Beispiele, es gibt viele Wege die zur Lösung führen)

### 1.1 Funktionen

```python
def combat(health, damage):
difference = health - damage
if difference < 0:
return 0
else return difference
print(combat(health=100, damage=20))
print(combat(health=10, damage=30))
```


Oder einfacher:

```python
def combat(health, damage):
return max(health - damage, 0)
```

```python
def abbrevName(name):
parts = name.split(" ")
return parts[0][0].upper() + "." +  parts[1][0].upper()
```

```python
def century(year):
return ((year-1) // 100) +1
```


### 1.2 Number guessing game
```python
user_eingabe = None
geheime_zahl = 42
while user_eingabe != geheime_zahl:
user_eingabe = int(input("Bitte gebe eine Zahl ein: "))
if user_eingabe > geheime_zahl:
print("Zu hoch geschätzt!")
elif user_eingabe < geheime_zahl:
print("Zu niedrig geschätzt!")
else:
print("Richtig")
```


2 Mengen
--------

Mengen sind ungeordnete Sammlungen von Objekten. Sie können kein Element mehrfach enthalten:

```python
my_numbers = {1, 2, 3, 4, 5, 5, 6, 6}
print(my_numbers)
```

```
{1, 2, 3, 4, 5, 6}
```

Wie auch bei Listen und Dictionaries gibt es eine Built-in Funktion die bestimmte Objekte in Mengen umwandeln kann. Nochmal zur Übersicht:

`list(...)`

`dict(...)`

`set(...)`

Erzeugen Listen, Wörterbücher und Mengen aus ihren Argumenten (wenn möglich).

```python
letter_set = set("A Python Tutorial")
print(letter_set)
meine_liste = ["A","B","C","A","B","C"]

leeres_wörterbuch = dict()

liste_ohne_duplikate = list(set(meine_liste))
```
```
{'y', 'u', 'h', 'r', 'i', 'l', 'P', 'n', 'a', 'T', ' ', 't', 'A', 'o'}
```
Weitere interessante Operationen mit sets sind die sogenannten Mengenoperationen.

```python
saeugetiere = {"löwe", "pferd", "eierlegende wollmilchsau", "schnabeltier", "giraffe", "affe"}
ovipare = {"rabe", "spatz", "eierlegende wollmilchsau", "schnabeltier", "tucan", "papagei"}

# Welche Tiere legen Eier und sind Säugetiere?

print(saeugetiere & ovipare)

# Welche tiere legen nur Eier

print(ovipare - saeugetiere)

# Welche tiere legen Eier, oder sind Säugetiere, aber nicht beides?

print(ovipare ^ saeugetiere)

# Alle tiere (Vereinigung beider mengen)

print(saeugetiere | ovipare)
```

```
{'eierlegende wollmilchsau', 'schnabeltier'}
{'papagei', 'tucan', 'spatz', 'rabe'}
{'pferd', 'giraffe', 'tucan', 'löwe', 'affe', 'spatz', 'papagei', 'rabe'}
{'affe', 'pferd', 'giraffe', 'tucan', 'spatz', 'löwe', 'papagei', 'rabe', 'eierlegende wollmilchsau', 'schnabeltier'}
```

### 2.1 Übung: gemeinsame Buchstaben

Die selbe Übung, in drei Schwierigkeitsgraden:

*   Deklariere zwei Zeichenketten `text_1` und `text_2`. Versuche dann die Buchstaben auszugeben, die in beiden Zeichenketten enthalten sind.
*   Schreibe eine Funktion `gemeinsame_buchstaben(text_1, text_2)`, welche diese gemeinsamen Buchstaben entweder ausgibt, oder als Rückgabewert liefert.
*   Schreibe ein Programm, welches zwei Zeichenketten vom User entgegennimmt, und dann die gemeinsamen Buchstaben ausgibt.

3 Objektorientierte Programmierung
----------------------------------

### 3.1 Klassen und Objekte

Zusammenhänge in der echten Welt sind sehr komplex. Computer hingegen sind eigentlich ziemlich doof: Sie können nur mit exakten Rechenregeln arbeiten und stumpf Befehle ausführen. Um die Welt "berechenbar" zu machen braucht man also immer ein Modell: Ein vereinfachtes Abbild der Wirklichkeit.

Objektorientierung ist eine Möglichkeit, Zusammenhänge zu modellieren. Die Grundidee ist, jede Sache in der echten Welt als Objekt mit einem Zustand und fest definiertem Verhalten darzustellen.

Klassen sind Baupläne für Objekte. Sie beschreiben, welche Funktionalität ein konkretes Objekt hat, und welche Zustände es besitzt. Objekte sind dann konkrete Instanzen von Klassen.

Wann ist also der Unterschied zwischen Datenstrukturen und Objekten? Datenstrukturen verstecken Funktionalität und bieten Daten an, Objekte bieten Funktionalität und verstecken Daten.

_Genauere Erklärung und Diskussion über OOP im Kurs_

```python
class Bike:

    def __init__(self, model, color):
        self.model = model
        self.color = color
        self.current_speed = 0

    def speed_up(self):
        self.current_speed += 5

    def slow_down(self):
        self.current_speed -= 5

    def brake(self):
        self.current_speed = 0

    def describe(self):
        print(self.model, "has color", self.color,
              ", current speed is", str(self.current_speed), "km/h")

mountain_bike = Bike("mountain bike", "black")
mountain_bike.speed_up()
mountain_bike.describe()

city_bike = Bike("city bike", "pink")
city_bike.speed_up()
city_bike.speed_up()
city_bike.speed_up()
city_bike.describe()
city_bike.brake()
city_bike.describe()
```
```
mountain bike has color black , current speed is 5 km/h
city bike has color pink , current speed is 15 km/h
city bike has color pink , current speed is 0 km/h
```

### 3.2 Übung: Objektorientiertes Bankkonto

Implementiert die Klasse `Bankkonto`.

*   Ein Bankkonto hat eine eindeutige ID und einen Kontostand (anfänglich 0)
*   Man kann einen bestimmten Betrag einzahlen und auszahlen
*   Man kann sich den aktuellen Kontostand ausgeben lassen

### 3.3 Übung (fortgeschritten): Piraterie

[https://www.codewars.com/kata/object-oriented-piracy](https://www.codewars.com/kata/object-oriented-piracy)

4 Weiterführend: Python lernen
------------------------------

Der erste Teil des Kurses ist vorbei und ihr möchtet alleine weitermachen? Kein Problem, es gibt eine Vielzahl von Möglichkeiten.

### 4.1 CodeCombat

Von einer Teilnehmerin empfohlen, kann man hier spielerisch am Ball bleiben: [Link](https://codecombat.com/play/)

### 4.2 Coding - Katas

Unter Entwicklern hat sich eine bestimmte Trainingsmethode etabliert: Die sogenannten Katas (der Begriff kommt aus dem Kampfsport). Hierbei schreibt ein Entwickler ein Problem auf, dass es zu lösen gilt. Zusätzlich schreibt der Herausforderer Test-Code der Überprüft, ob das Problem richtig gelöst wurde. Der andere Entwickler muss dann versuchen, das Problem so zu lösen dass der Test erfolgreich verläuft.

Es gibt eine Website, auf der man diese Katas in allen Schwierigkeitsgraden lösen kann: [www.codewars.com](http://www.codewars.com/r/iQ48PQ). Meldet euch gerne dort an (wenn ihr wollt, tretet dem Clan "moinworld" bei). Eine unterhaltsame Möglichkeit zum Üben :)

Viele Aufgaben aus diesem Kurs habe ich übrigens von dieser Website. Hier die komplette Liste, falls ihr dafür die Punkte holen wollt:

[https://www.codewars.com/kata/drink-about/python](https://www.codewars.com/kata/drink-about/python)

[https://www.codewars.com/kata/thinkful-logic-drills-traffic-light](https://www.codewars.com/kata/thinkful-logic-drills-traffic-light)

[https://www.codewars.com/kata/sum-of-multiples](https://www.codewars.com/kata/sum-of-multiples)

[http://www.codewars.com/kata/century-from-year/train/python](http://www.codewars.com/kata/century-from-year/train/python)

[http://www.codewars.com/kata/grasshopper-terminal-game-combat-function-1/train/python](http://www.codewars.com/kata/grasshopper-terminal-game-combat-function-1/train/python)

[http://www.codewars.com/kata/abbreviate-a-two-word-name/train/python](http://www.codewars.com/kata/abbreviate-a-two-word-name/train/python)

Für unser Erfahrungslevel sind Kata der Schwierigkeitsstufe 8 und 7 (sprache Python!) geeignet.

[http://www.codewars.com/kata/search/python?q=&r%5B%5D=-8&r%5B%5D=-7&beta=false](http://www.codewars.com/kata/search/python?q=&r%5B%5D=-8&r%5B%5D=-7&beta=false)

### 4.3 Online - Kurse

Generell eine gute Resource um selbst zu lernen ist der Kurs von codecadamy: [https://www.codecademy.com/learn/learn-python](https://www.codecademy.com/learn/learn-python) Dort gibt es interaktive Erklärungen zum Stoff und auch Übungsaufgaben die ganz genau erklärt und mit Hinweisen bestückt sind. Aber vorsicht: Dieser Kurs lehrt die Python Version zwei. Ist aber wie bereits erwähnt nicht schlimm, da der Unterschied zwischen Python 2 und 3 nicht groß ist. Es gibt auch einen Kurs für Python3, Kostet aber ziemlich viel (Mitgliedschaft für ~ 20€ /Monat), immerhin gibt es eine kostenlose 7 Tage mitgliedschaft.

Darüber hinaus gibt es noch unzählige Kurse, sogar mobile Apps zum Lernen. Die habe ich natürlich nicht alle ausprobiert, aber generell sind solche Kurse zumindest vom Inhalt in guter Qualität. Das beste ist, etwas zu suchen was einem Spass macht und voran bringt.

### 4.4 Eigene Projekte

Für die Motivation super: Ein eigenes Projekt ausdenken (nicht zu schwierig!) und einfach kraft Suchmaschine und Entwicklerforen wie stackoverflow.com / moinworld slack umsetzen.