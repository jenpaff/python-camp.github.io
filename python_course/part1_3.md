---
layout: default
---

Baustein 1 Meeting 3
====================

*   [1. Lösungen zu den letzten Aufgaben](#1-lsungen-zu-den-letzten-aufgaben)
    *   [1.1. Sternenpyramide](#11-sternenpyramide)
    *   [1.2. Zahlenmuster](#12-zahlenmuster)
*   [2. Listen](#2-listen)
    *   [2.1. Sortieren](#21-sortieren)
    *   [2.2. Negative Indexe](#22-negative-indexe)
    *   [2.3. Übung - Sortieren und negative Indexe](#23-bung---sortieren-und-negative-indexe)
    *   [2.4. Slicing](#24-slicing)
    *   [2.5. Übung - Slicing](#25-bung---slicing)
*   [3. Funktionen](#3-funktionen)
    *   [3.1. Übung: Hangman](#31-bung-hangman)
*   [4. Wörterbücher](#4-wrterbcher)
*   [5. User-Eingaben](#5-user-eingaben)
    *   [5.1. Übung - Interaktives Hangman spiel](#51-bung---interaktives-hangman-spiel)
    *   [5.2. Übung - Wörterbücher und Nutzereingaben](#52-bung---wrterbcher-und-nutzereingaben)
*   [6. Wiederholung](#6-wiederholung)
    *   [6.1. Funktionen](#61-funktionen)
    *   [6.2. Fortgeschritten: Number Guessing Game](#62-fortgeschritten-number-guessing-game)


1 Lösungen zu den letzten Aufgaben
----------------------------------

(Alle Lösungen sind nur Beispiele, es gibt viele Wege die zur Lösung führen)

### 1.1 Sternenpyramide

```python
i = 0
while i < 10:
i += 1
print("\*" * i)
while i > 0:
i -= 1
print("\*" * i)
```

```
\*
\*\*
\*\*\*
\*\*\*\*
\*\*\*\*\*
\*\*\*\*\*\*
\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*
\*\*\*\*\*\*
\*\*\*\*\*
\*\*\*\*
\*\*\*
\*\*
\*
```


oder auch:
```python
for i in range(1, 10):
print("\*" * i)
for i in range(10, 0, -1):
print("\*" * i)
```

```
\*
\*\*
\*\*\*
\*\*\*\*
\*\*\*\*\*
\*\*\*\*\*\*
\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*\*
\*\*\*\*\*\*\*
\*\*\*\*\*\*
\*\*\*\*\*
\*\*\*\*
\*\*\*
\*\*
\*
```

### 1.2 Zahlenmuster

```python
for i in range(1, 10):
print(str(i) * i)
```

```
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

2 Listen
--------

Beim letzten Kurs haben wir die Grundlagen schon kennengelernt. Es folgt ein Ausblick, was Listen alles noch können.

### 2.1 Sortieren

Eine Liste alphabetisch oder numerisch zu sortieren kann häufiger mal nützlich sein. Das kann python bereits:

```python
zahlen = [1, 5, 7, 4, 10, 26, 2, 42]
zahlen.sort()
print(zahlen)
```
```
[1, 2, 4, 5, 7, 10, 26, 42]
```

Es gibt auch eine builtin-Funktion, die das Ergebnis direkt zurückgibt:
```python
zahlen = [1, 5, 7, 4, 10, 26, 2, 42]
print(sorted(zahlen))
```

```
[1, 2, 4, 5, 7, 10, 26, 42]
```


### 2.2 Negative Indexe

Wenn man sich für ein Element am Ende einer Liste interessiert (z.B. das vorletzte), kann man dies mit einem negativen Index holen:

```python
# -8 -7 -6 -5  -4  -3            -2             -1
zahlen = [1, 5, 7, 4, 10, 26, "interessantes element", 42]
print(zahlen[-2])
```
```
interessantes element
```

### 2.3 Übung - Sortieren und negative Indexe

Versucht nun sortieren und negative Indexe zu kombinieren, um die zwei größten Zahlen aus einer Liste herauszufinden.

### 2.4 Slicing

Wie im letzten Kurs schon kurz angerissen, kann es hilfreich sein nur bestimmte Ausschnitte von Listen zu bearbeiten.

`a[start:end]` Elemente von start bis end-1

`a[start:]` Elemente ab start

`a[:end]` Elemente vom Anfang bis end-1

`a[:]` Komplette Kopie eines Arrays

`a[start:end:step]` Elemente von start bis end-1 mit Schrittgröße step

```python
zahlen = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

print(zahlen[1:7])
print(zahlen[5:])
print(zahlen[:5])
print(zahlen[1:7:2])
print(zahlen[7:1:-1])
```

```
[1, 2, 3, 4, 5, 6]
[5, 6, 7, 8, 9, 10]
[0, 1, 2, 3, 4]
[1, 3, 5]
[7, 6, 5, 4, 3, 2]
```


### 2.5 Übung - Slicing

Ihr schreibt eine Software für einen Supermarkt. In jedem Kassiervorgang kommt die Rechnung für einen Kunden in der folgenden Form:

`basket = ['cucumber', 12, 'pickles', 4, 'sugar', 8, 'rice', 17]`

D.h. es steht immer Produkt gefolgt von Preis in der Liste. Berechnet mit einem Python-Programm die Summe der Preise in einer basket-Liste. Hinweis: die builtin-funktion `sum` kann da hilfreich sein, sie nimmt eine Liste an Zahlen entgegen und gibt die Summe zurück.

3 Funktionen
------------

Funktionen sind wiederverwendbare Codeblöcke mit fest definierten Eingabeparametern und Ausgabewerten. Das Schlüsselwort def leitet die Funktionsdeklaration ein. Darauf folgt der Funktionsname gefolgt von Parametern in geschweifeten Klammern. Parameter sind Platzhalter die erst beim Aufruf einer Funktion durch konkrete Werte ersetzt werden. Eine Funktion kann beliebig viele Parameter (mit Komma getrennt) haben. Im nachfolgenden Codeblock findet die Berechnung der Funktion statt. Wenn es dabei Ergebnisse gibt Nachfolgend sind einige Beispiele:

```python
def greet_user():
print("Hello World!")

greet_user()

def greet_user(username):
print("Hello " + username + ". Welcome to the Website!")

greet_user("Kurt")

def calculate_prize(prize, versandart):
if versandart == "premium":
prize += 5
else:
prize += 1
return prize

gesamtpreis = calculate_prize(prize=12, versandart="premium")
print(gesamtpreis)
```
```
Hello World!
Hello Kurt. Welcome to the Website!
17
```

### 3.1 Übung: Hangman

Ziel dieser Übung ist es eine Funktion `zeige_wort` für das Spiel "Hangman" zu schreiben. Diese Funktion nimmt ein wort und eine Liste geratener Buchstaben entgegen. Das Wort wird auf dem Bildschirm ausgegeben, wobei aber noch nicht erratene Buchstaben mit einem `_` ersetzt werden.

Beispiel:

```
zeige_wort("schifffahrt", ['f', 's', 'h'])
```

Sollte `s_h_fff_h__` ausgeben.

Wichtige tipps:

*   Mit der `for` schleife kann man die einzelnen Buchstaben einer Zeichenkette durchlaufen
*   mit print("_", end="") kann man einzelne Buchstaben auf der Konsole ausgeben
*   Ob ein Buchstabe in einer Liste vorhanden ist, könnt ihr mit dem `in` Schlüsselwort herausfinden. Beispiel:

```python
print("a" in ["a", "b", "c"])
print("d" in ["a", "b", "c"])
```

```
True
False
```

Die Aufgabestellung in anderen Worten:

Für jeden Buchstaben im Wort:

*   wenn dieser geraten wurde (in der Liste enthalten ist), gebe ihn aus,
*   wenn nicht gebe einen Unterstrich aus.

4 Wörterbücher
--------------

Wörterbücher (englisch Dictionaries) sind praktische Datenstrukturen. Sie speichern Daten unter einem Schlüssel ab (im Gegensatz zu einem Index bei einer Liste. Wichtig ist dabei, dass die Schlüssel eindeutig sind.

Mit einem Wörterbuch können wir zum Beispiel einen Wetterbericht speichern: Eine Zuordnung von Postleitzahl zu Temperatur zum Beispiel. Oder eine Zuordnung von englischen zu deutschen Wörtern, also buchstäblich ein Wörterbuch.

```python
wetterbericht = {"21337" : 22, "20355": 27, "12345": 17}
woerterbuch = {"cat": "Katze", "platypus": "Schnabeltier", "rain" : "Regen"}
# Zugriff
print(woerterbuch["cat"])

# Verändern oder einfügen
woerterbuch["cat"] = "Tiger"
print(woerterbuch)

# Löschen
del woerterbuch["cat"]
print(woerterbuch)
```
```
Katze
{'cat': 'Tiger', 'platypus': 'Schnabeltier', 'rain': 'Regen'}
{'platypus': 'Schnabeltier', 'rain': 'Regen'}
```

Wenn ein Schlüssel im Wörterbuch nicht gefunden wird, dann stürzt euer Programm mit einem Fehler ab! Dies kann man durch eine vorherige Prüfung absichern.

```python
if "cat" in woerterbuch:
print(woerterbuch["cat"])
```
### 4.1 Übung - Wörterbücher und Funktionen

Schreibe eine Funktion "translate", die zu einem gegebenen Wort die Übersetzung aus dem Wörterbuch ausgibt. Wenn das Wort nicht gefunden werden konnte, gib sie "Das Wort konnte leider nicht gefunden werden":

```python
woerterbuch = {"cat": "Katze", "platypus": "Schnabeltier", "rain" : "Regen"}
# ...
```

5 User-Eingaben
---------------

User - Input in einem Programm holt man sich in Python ganz einfach mit der Funktion input(). Sie lässt einen Blinkenden Cursor im Konsolenfenster erscheinen, und wenn der User mit Enter seine Eingabe bestätigt, liefert sie die Eingabe als Zeichenkette. Zum Beispiel so:

wort = input()
print(wort)

Man kann der Funktion input() selbst eine Zeichenkette übergeben, diese wird dann als Hinweis an den Nutzer angezeigt.

username = input("Bitte geben Sie Ihren Benutzernamen ein: ")
print("Eingegebener Benutzername: " + username)

### 5.1 Übung - Interaktives Hangman spiel

Entwickelt ein richtiges Hangman (Galgenmännchen) spiel. Dafür könnt ihr die Funtion aus der vorherigen Aufgabe (`zeige_wort`) nehmen. Die Entwicklung des Spiels teilt Ihr am Besten in mehrere Schritte.

*   Zunächst soll es möglich sein, in einer Endlosschleife das Wort zu vervollständigen.

Hier ist eine Vorlage für das Spiel in einer Endlosschleife:

```python
geraten = []
geheimwort = "schifffahrt" # zur Einfachheit alles in kleinbuchstaben
while True:
eingabe = input()
geraten.append(eingabe)
# Hier zeige_wort mit den richtigen parametern aufrufen!
```

*   Nun soll "Game Over" mit eingebaut werden. Wenn die anzahl der geratenen Buchstaben

(denkt dran, mit `len` kann man die Länge einer Liste herausfinden) `10` überschreitet, soll das spiel abgebrochen werden.

*   Bonuspunkte gibt es noch, wenn das Spiel auch abbricht, wenn man gewonnen hat.

Tipp: Ihr müsst dafür die Bedingung in der while schleife anpassen.

### 5.2 Übung - Wörterbücher und Nutzereingaben

Wir schreiben ein interaktives Wörterbuch. Dazu gibt der Nutzer ein gesuchtes Wort ein. Ist das eingegebene Wort im Wörterbuch vorhanden, wird die Übersetzung ausgegeben. Wenn nicht, wird eine Fehlermeldung ausgegeben. In jedem fall wird der Nutzer erneut nach einer Eingabe gefragt, bis er "quit." eingibt. Dazu definiert ihr euch zunächst ein beliebiges Wörterbuch, zum Beispiel das von vorhin:

```python
woerterbuch = {"cat": "Katze", "platypus": "Schnabeltier", "rain" : "Regen"}
# ...
```

Vielleicht ist es hier hilfreich, sich erstmal keine Gedanken über den Abbruch der schleife bei `quit`. zu machen. Ihr könntet erstmal mit einer Endlosschleife Anfangen:

```python
while True:
user_input = input("Bitte gesuchtes wort eingeben")
...
```

6 Wiederholung
--------------

### 6.1 Funktionen

Implementiert Funktionen, welche die folgenden Spezifikationen erfüllen (Oder sucht euch eine aus):

1.  Schreibt euch eine Funktion combat mit den Parametern Gesundheit (health) eines Spielers und Schaden (damage) den der Spieler nimmt. Als Rückgabewert soll die Differenz zwischen health und damage zurückgeben. Ist diese Differenz allerdings negativ, soll 0 zurückgegeben werden.
2.  Die zweite Funktion soll als Parameter einen Namen als Zeichenkette in dem Format “Vorname Nachname” bekommen. Als Rückgabewert liefert sie die Initialien dieses Namens. So wird aus “Gregor Strobel” “G.S” und “Günter Jauch” “G.J”. Ist der Name kleingeschrieben sollen die Initialien trotzdem groß sein!
3.  Die dritte funktion bekommt eine Jahreszahl als Integer und gibt das Jahrhundert zurück. Merke: Das erste Jahrhundert spannt von Jahr 1 - 100, das zweite von 101 - 200 usw. Ein paar Beispiele: centuryFromYear(1705) ergibt 18 centuryFromYear(1900) ergibt 19 centuryFromYear(1601) ergibt 17

### 6.2 Fortgeschritten: Number Guessing Game

Definiert euch eine geheime Zahl mit beliebigem Wert. Der User soll jetzt in einer Schleife nach einer Zahl gefragt werden. Hat er richtig geraten, bricht die Schleife ab. Wenn er zu klein oder zu groß rät, bekommt er einen Hinweis und darf erneut raten. Zum Beispiel könnte eine Beispielsitzung mit dem Programm so aussehen.

```
Rate eine Zahl
5
Falsch, zahl zu klein geraten!
Rate eine Zahl
72
Falsch, zu groß geraten
Rate eine Zahl
40
Falsch, zahl zu klein geraten!
Rate eine Zahl
42
Richtig!
```
