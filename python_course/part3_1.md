---
layout: default
---

Baustein 3 Meeting 1
====================

*   [1\. Warmup](#sec-1)
    *   [1.1. Übung: FLAME game](#sec-1-1)
*   [2\. Objektorientierte Programmierung](#sec-2)
    *   [2.1. Wiederholung der Basics](#sec-2-1)
    *   [2.2. Übung (Funktionen+Objekte): Trip-Kosten](#sec-2-2)

Willkommen zum Python Kurs 3! In den vier Terminen geht es darum Python in der Tiefe kennenzulernen, aber auch genereller um das algorithmische Lösen von Problemen.

*   Ich verwende im Kurs die IDE [thonny](https://thonny.org), welche gut für Anfänger geeignet ist. Ihr könnt aber gerne eure eigene Entwicklungsumgebung verwenden.
*   Bei Abwesenheit können wir die Sitzungen aufnehmen (wenn alle einverstanden sind), sagt einfach bescheid.
*   Wie auch in den letzten Kursen ist ein Teil der Übungen von [codewars](http://www.codewars.com/r/iQ48PQ) "katas" inspiriert. Diese sind entsprechend verlinkt. Ihr könnt gerne auch auf der Website trainieren ([**klick**](http://www.codewars.com/r/iQ48PQ)), um zu prüfen ob eure Lösungen korrekt sind, und andere Lösungen zu sehen, müsst es aber nicht.

1 Warmup
--------

### 1.1 Übung: FLAME game

Schreibt eine Funktion `flame_game(name1, name2)`, welche zwei Namen als Zeichenkette entgegennimmt, und dann den Status der Liebesbeziehung zwischen diesen zwei Namen ausgibt.

Der Status wird so berechnet:

*   Erst werden alle Buchstaben entfernt die in beiden Zeichenketten enthalten sind

(Groß-Kleinschreibung wird nicht beachtet).

*   Die Länge der beiden Zeichenketten wird addiert.
*   Die Entstehende Zahl wird verwendet um die Antwortoption auszugeben.

Ist die Zahl größer als 6 geht es wieder von vorne los.
```
F = Friendship (1)
L = Love (2)
A = Affection (3)
M = Marriage (4)
E = Enemies (5)
S = Siblings (6)
```

Beispiel:

```python
flame_game("NEIL", "MAGDALENA") # Enemies
```

*   Duplikate entfernen: I, MAGDAA
*   Längen addieren: (1 + 6 = 7)
*   7 Steht für "Friendship" (7 Ist hinter der 6, es geht also ab da von vorne los)

[(referenz, nur Java)](https://www.codewars.com/kata/553e0c3c8b8c2e1745000005)

2 Objektorientierte Programmierung
----------------------------------

### 2.1 Wiederholung der Basics

Objektorientierte Programmierung bezeichnet ein Methode für die Strukturierung von Programmen. Hierbei werden Zustände und Funktionalität in Objekte gekapselt und das Programm somit in Komponenten aufgeteilt. Diese Vorgehensweise, richtig angewandt, verbessert die Wiederverwendbarkeit, Lesbarkeit und Wartbarkeit von Programmcode.

[Wiederholung aus Kurs 1](part1_4.html)

### 2.2 Übung (Funktionen+Objekte): Trip-Kosten

Die nächste Urlaubsplanung steht an, und ihr wollt mit euren Freunden eine Roadtrip in den USA machen. Amerika hat komische Gesetze, zum Beispiel dass sich die Kosten eines Hotels (für eine Nacht) aus der Anzahl der Vokale `(aeiou)` berechnet. Dafür schreibt ihr erstmal eine Funktion `hotel_cost(hotel_name)` die die Anzahl von Vokalen im Namen zurück gibt. Beispiel:

```python
print(hotel_cost("alabama inn")) # 5
```

Um die Nächte und Anzahl an Personen für den Trip zu speichern, habt ihr schon eine Klasse geschrieben:

```python
class Stay:

    def __init__(self, hotel, nights, people):
        self.hotel = hotel
        self.nights = nights
        self.people = people
```

Jetzt müsst ihr nur noch eine Funktion `trip_cost(stays)` schreiben, um die Gesamtkosten der Reise zu berechnen. Beispiel:

```python
print(trip_cost([Stay("alabama inn", 6, 2), Stay("kentucky ranch", 3, 5)])) # 105
```

Tipps:

*   Um auf ein Attribut eines Objekts zuzugreifen, einfach die Punktnotation verwenden:

```python
my_stay = Stay("alabama inn", 6, 2)
print(my_stay.hotel)
```

*   Um zu prüfen ob ein Buchstabe ein Vokal ist:

```python
print("a" in "aeiou")
print("c" in "aeiou")
```

```
True
False
```