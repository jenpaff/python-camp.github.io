---
layout: default
---

Baustein 3 Meeting 1
====================

* [1\. Objektorientierte Programmierung (forts.)](#sec-1)
    * [1.1. Übung: Highscore Liste](#sec-1-1)
    * [1.2. Vererbung](#sec-1-2)
* [2\. Higher order Funktionen, Lambda-Funktionen](#sec-2)


1 Objektorientierte Programmierung (forts.)
-------------------------------------------

### 1.1 Übung: Highscore Liste

Ihr programmiert ein neues Spiel "Kampf gegen den Kakadu", und wollt dem Spieler mit einer typischen Highscore-Liste einen Anreiz geben sich wieder und wieder zu verbessern.

* Bei der Erzeugung der Liste wird die maximale Größe angegeben
* Die Methode `update` nimmt eine neue Punktezahl auf und fügt sie der Liste hinzu.

Dabei soll die Liste stets sortiert sein, und nie die Maximalkapazität überschreiten.

* Reset löscht die gesamte Liste.

```python
highScoreTable = HighScoreTable(3)
print(highScoreTable.scores) # []
highScoreTable.update(10)
print(highScoreTable.scores) # [10]
highScoreTable.update(8)
highScoreTable.update(12)
highScoreTable.update(5)
highScoreTable.update(10)
print(highScoreTable.scores) # [12, 10, 10]
highScoreTable.reset()
print(highScoreTable.scores) # []
```

[(referenz)](https://www.codewars.com/kata/5962bbea6878a381ed000036)

### 1.2 Vererbung

* Einige Klassen haben Gemeinsamkeiten und Unterschiede
* Die Gemeinsamkeiten wollen wir nicht doppelt in Code ausdrücken
* Deshalb erstellen wir eine “Elternklasse” mit den Gemeinsamkeiten und “erben” davon.
* Wir können dabei methoden der Überklasse aufrufen, dies gilt auch für `__init__`.

```python
class Animal:

    def \_\_init\_\_(self, name, age):
        self.name = name
        self.age = age

    def eat(self):
        print(self.name + " isst etwas.")

    def move(self):
        print(self.name + " bewegt sich.")

class Bird(Animal):

    def fly(self):
        print("Ich kann flieeeegen - " \+ self.name + ".")

class Dog(Animal):

    def bark(self):
        print("Woof Woof")

class Mops(Dog):

    def bark(self):
        super().bark()
        print("fiep")

class Parrot(Bird):

    def \_\_init\_\_(self, name, age, color):
        super().\_\_init\_\_(name, age)
        self.color = color

loewe = Animal("Löwe", 5)
loewe.eat()
loewe.move()
print("-------------")
doggie = Dog("Doggie", 7)
doggie.bark()
doggie.eat()
print("-------------")
ruffi = Mops("Ruffi", 3)
ruffi.eat()
ruffi.bark()
```
```
Löwe isst etwas.
Löwe bewegt sich.
-------------
Woof Woof
Doggie isst etwas.
-------------
Ruffi isst etwas.
Woof Woof
fiep
```

2 Higher order Funktionen, Lambda-Funktionen
--------------------------------------------

In Python können Funktionen genau so wie andere Werte als Variablen weitergegeben und in Datenstrukturen (z.B. Listen) gespeichert werden. Zum Beispiel wenn man Funktionen an Bibliotheken weitergibt, braucht man diese nur ein einziges mal. Dafür will man sich nicht jedes mal einen Namen ausdenken. Ein klassisches Beispiel dafür ist das Sortieren.

Die `sorted` Funktion, welche ihr bereits kennt, kann eine Datenstruktur sortieren. Wir haben schon gesehen, wie man Listen aufsteigend und absteigend sortieren kann. Aber was ist, wenn wir unsere eigene Reihenfolge festlegen wollen?

Angenommen, wir haben folgende Spieler-Klasse für _Kampf gegen den Kakadu_ geschrieben.

class Player:
def __init__(self, level, name):
self.level = level
self.name = name

Jetzt wollen wir in der UI nur die Spieler nach Level sortiert anzeigen. Wie machen wir dass?

class Player:
def __init__(self, level, name):
self.level = level
self.name = name
def __repr__(self):
return self.name + ", level: " + str(self.level)
players = [Player(42, "birdlover2000"), Player(69, "warrior420"), Player(11, "gigagünter")]
print(sorted(players, key=lambda player: player.level))
players = [Player(42, "birdlover2000"), Player(69, "warrior420"),  Player(11, "abchero"), Player(11, "gigagünter")]
print(sorted(players, key=lambda player: [player.level, player.name]))

[gigagünter, level: 11, birdlover2000, level: 42, warrior420, level: 69]
[abchero, level: 11, gigagünter, level: 11, birdlover2000, level: 42, warrior420, level: 69]

Wir geben eine anonyme Funktion an, die ein `Player`-Objekt in eine Zahl, Zeichenkette, oder in irgendwas das den `<`-Operator unterstützt umwandelt. So kann Python diese Funktion auf jedes Objekt anwenden, und dann die Sortierreihenfolge entscheiden.

Übrigens: Mann kann den `<` Operator auch direkt für eine Klasse definieren:

```python
class Player:
def __init__(self, level, name):
self.level = level
self.name = name
def __repr__(self):
return self.name + ", level: " + str(self.level)
def __lt__(self, other):
return self.level < other.level
players = [Player(42, "birdlover2000"), Player(69, "warrior420"), Player(11, "gigagünter")]
print(sorted(players)
```