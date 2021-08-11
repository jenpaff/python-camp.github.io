---
layout: default
---

Baustein 2 Meeting 1
====================

*   [1\. Wiederholung](#1-wiederholung)
    *   [1.1. Teil 1: Variablen und Datentypen, Rechnen](#11-teil-1-variablen-und-datentypen-rechnen)
    *   [1.2. Teil 2: while - Schleife, Bedingungen](#12-teil-2-while---schleife-bedingungen)
    *   [1.3. Teil 3: Funktionen, Listen, For - Schleifen](#13-teil-3-funktionen-listen-for---schleifen)
    *   [1.4. Teil 4: Objektorientierung](#14-teil-4-objektorientierung)
    

Herzlich wilkommen zum zweiten Teil des Kurses! Nachdem wir die Grundlagen des Programmierens kennengelernt haben, liegt der Fokus in diesem Abschnitt auf dem Sammeln von Erfahrungen und dem Entdecken von coolen Dingen die man mit Python tun kann. In den letzten zwei Stunden implementieren wir ein richtiges Projekt! Welches Projekt das sein soll könnt ihr selber über eine Abstimmung in Slack festlegen. Eigene Ideen könnt ihr auch gerne an mich senden.

1 Wiederholung
--------------

Wiederholung ist wichtig fürs erfolgreiche Lernen! In dem heutigen warm-up gehen wir zu jedem der Themenbereiche aus dem ersten Kurs eine Aufgabe durch.

### 1.1 Teil 1: Variablen und Datentypen, Rechnen

Die erste Zeile ist vorgegeben: Ihr findet eine Variable `temperatur_c` mit einer Kommazahl als `string` vor. Rechnet diese Temperatur in Kelvin um (+ 273.15) und gebt in einer lesbaren Nachricht die Temperatur in Kelvin aus, zum Beispiel: Die aktuelle Temperatur ist x Kelvin.

```python
temperatur_c = 10.12
# euer code ...
```

### 1.2 Teil 2: while - Schleife, Bedingungen

Gegeben sein eine Zahl n. Schreibt eine while - Schleife, die solange Folgendes ausführen soll, bis n den Wert 1 bekommt:

*   wenn n ungerade ist, multipliziere n mit 3 und addiere 1
*   wenn n gerade ist, teile n durch 2

Der Wert von `n` soll in jedem Schleifendurchlauf ausgegeben werden. Zur Erinnerung: Die Teilbarkeit einer Zahl n durch m lässt sich in python mittels Teilung mit Rest (modulo) `n % m == 0` bestimmen. (by the way: Die Frage ob diese Schleife für jede Zahl `n` terminiert, ist ein [bisher ungelöstes Problem](https://www.youtube.com/watch?v=5mFpVDpKX70)).

```python
n = 42
while ...:
# euer code
```

([Lösung](https://falcowinkler.github.io/resources/python-course/kurs_2_1_wiederholung_schleifen.py))

### 1.3 Teil 3: Funktionen, Listen, For - Schleifen

Diese Aufgabe kombiniert viele der bisherigen Konzepte. Ihr sollt eine Funktion `punkte` schreiben, welche die Punktezahl für einen multiple-choice test ausgibt. Genauer gesagt nimmt diese Funktion zwei Listen als Parameter an. Beide der Listen enthalten Buchstaben von a bis d, in der ersten Liste stehen die Lösungen, in der zweiten Liste die Antworten. Eine falsche Antwort gibt -1 Punkt, eine richtige gibt +4 Punkte.

```python
loesungen = \["a", "a", "b", "b"\]
antworten = \["a", "c", "b", "d"\]
```

Ein Hinweis: Um beide Listen miteinander zu vergleichen, gibt es die praktische Built-in Funktion `zip`. Diese kombiniert zwei Listen wie ein Reisverschluss, und liefert uns paare mit dem selben index, durch die wir iterieren können.

```python
loesungen = \["a", "a", "b", "b"\]
antworten = \["a", "c", "b", "d"\]
for loesung, antwort in zip(loesungen, antworten):
print(loesung == antwort)
```

```
True
False
True
False
```

([Lösung](https://falcowinkler.github.io/resources/python-course/kurs_2_1_wiederholung_punktezahl.py))

### 1.4 Teil 4: Objektorientierung

Erinnert ihr euch noch an das [Number Guessing Game aus Baustein 1?](https://falcowinkler.github.io/part1_3.html#sec-6-2) Das Spiel wollen wir jetzt so erweitern, dass man eine bestimmte Anzahl an "Leben" fürs Raten hat. Wir schreiben dafür eine Klasse `GuessingGame` die

*   im Konstruktor (`__init__`) die geheime Zahl als Parameter annimmt und in `self` speichert,

die Anzahl an Leben wird inital immer auf 10 gesetzt.

*   eine Methode `guess` bereitstellt die eine Zahl als Parameter annimmt, und eine Zahl zurückgibt: -1 für zu klein 0 für richtig, 1 für zu gross.
*   eine Methode `is_game_over` bereitstellt, die zurückgibt, ob die Anzahl an Leben kleiner oder gleich 0 ist (also entweder `True` oder `False`).

Als Zusatz könntet ihr jetzt noch ein interaktives Number Guessing game mithilfe dieser Klasse schreiben. Übrigens: Diese Version des Spiels mag vielleicht unnötig kompliziert erscheinen, stellt aber ein wichtiges wiederkehrendes Prinzip vor, dass euch dabei hilft, guten Code zu schreiben: Logische Entitäten in unserem Programm sollen möglichst _modular_, also austauschbar, gehalten werden. Hier haben wir die Spielelogik von der Nutzeroberfäche getrennt. ([Lösung](https://falcowinkler.github.io/resources/python-course/kurs_2_1_wiederholung_guessing_game.py))