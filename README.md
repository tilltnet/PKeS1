<!--

author:   Konstantin Kirchheim

email:    konstantin.kirchheim@ovgu.de

version:  1.0.0

language: de_DE

narator:  Deutsch Female

-->

# Einführung

--{{1}}--
Willkommen zurück im eLearning-System *eLab*. Da ihr euch während der letzten Aufgabe sowohl mit dem System, als auch mit dem Arbeitsablauf vertraut machen konntet, wird es in dieser Aufgabe darum gehen, tiefer in die Programmierung eingebetteter Systeme einzudringen. 

--{{2}}--
Ein wesentliches Merkmal eingebetteter Systeme ist, dass sie durch periphäre Hardware mit ihrer Umgebung interagieren können. Dafür müssen diese Hardwarekomponenten jedoch in Software repräsentiert und angesprochen werden können. Wie auch bei einem Desktop-Computer, geschieht dies bei eingebetteten Systemen durch Treiber.

--{{3}}--
Zur Einführung in die Treiberentwicklung eingebetteter Systeme, wird es in dieser Aufgabe darum gehen, die Funktionalität zur Ansteuerung eines 8-Segment-Displays zu Implementieren.


## Themen und Ziele

**Themen:**

* Ansteuerung periphärer Geräte durch einen Mikrocontroller
* Kapselung Gerätespezifischer Informationen in abstrahierenden Funktionen (Treiberentwicklung)
* Nutzung von Treibern zur Umsetzung einfacher Funktionalitäten

**Ziel(e):**

* Programmierung von Hardwareschnittstellen


## Weitere Informationen

**Treiber und Treiberentwicklung:**

* [Treiber](https://en.wikipedia.org/wiki/Device_driver)
* Datenblatt Display



**Assembler**
* [AVR GCC Inline Assembler Cookbook](http://www.nongnu.org/avr-libc/user-manual/inline_asm.html)

**Debugging**
* [Zweierkomplement](https://de.wikipedia.org/wiki/Zweierkomplement)
* [Serial.print()](https://www.arduino.cc/en/Serial/Print)


# Aufgabe 1

--{{1}}--
In der *ersten* praktischen Aufgabe sollt ihr zunächst einen Treiber für das 8-Segment-Display implementieren, bevor ihr in der zweiten Teilaufgabe basierend auf diesem Treiber einen Zähler auf diesem Display darstellt. 

**Teilaufgaben:**

* *1.1:* Implementiert die Grundfunktionalität zum Ansteuern des 8-Segment-Displays.
* *1.2:* Implementiert einen Zähler, der den auf dem 8-Segment-Display angezeigten Wert kontinuierlich inkrementiert.
* *(1.3:)* Macht den Zähler robust.


## Aufgabe 1.1 

**Ziel:**
Das Ziel der Aufgabe ist es, euch eine Einführung in die Grundlagen der Treiberentwicklung für eingebettete Systeme zu geben. Zusätzlich sollt ihr das Arbeiten mit den Datenblättern lernen.


**Teilschritte:**

1. Zunächst müsst ihr das Macro `PKES_TASK` auf den Wert `1` setzten, damit der Code der ersten Aufgabe in das Kompilat übernommen wird.
``` c
#define PKES_TASK		(1) // <-- change here 

// ... 

#if PKES_TASK >= 1
	// some code for task 1 
#endif 
```
2. Lest und versteht den Code der Vorlage. 

3. Recherchiert in den Datenblättern, wie das Display angesteuert werden kann.

4. Implementiert die Grundfunktion
   * `void writeDigitsToDisplay(char digit1, char digit2, char digit3)` 

5. Implementiert die erweiterten Funktionen  
   * `void writeValueToDisplay(int value)` 
   * `void writeValueToDisplay(float value, char dec)`
   Diese sollen  den Funktionsaufruf lediglich an die Grundfunktion weiterreichen. 









## Aufgabe 1.2 

**Ziel:**
Ihr habt diese Aufgabe erfolgreich abgeschlossen, wenn euer Bot einen Zähler von -99 bis 99 anzeigt. Bei einem Überlauf soll der Zähler zum entgegengesetzten maximalwert springen. Der Zähler soll sich immer um den Wert in der lokalen variable `step_res` verändern. 


**Teilschritte:**

1. Lest und versteht den Code in der Vorlage 

2. Implementiert die Funktion 
   * `signed char refreshIntCounter(signed char counter)`
   in **Assembler**. 
   Ihr könnt euch dabei an der Funktion `float refreshFloatCounter(float counter)` orientieren. 




## Bonusaufgabe 1.3

Sorgt dafür, dass der Zähler aus der vorherigen Aufgabe auch dann funktioniert, wenn man der  `step_res` Variable negative Werte zuweist.  



