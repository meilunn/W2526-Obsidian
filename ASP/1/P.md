# Abstraktion

- Viele Schichten
- Häufig auch gut versteckt, z.B. syntax-Fehler in Java verursacht wall of text stack trace -> jede Ebene wirft Fehler
- Haben (meist) Performance-Overhead -> Laufzeit, Speicherbedarf, …
- Scheinen manchmal durch, sodass man sie sieht -> "leak"
	- z.B. komische Performanzeffekte, Debugging von bereits optimiertem Code, 500+ Lines Stack Trace

> Hardware wird immer schneller
- Physikalische Grenzen -> stagnation

> Always test performance after optimising!

----

# Prozessor und Speicher

- Steurungs- und Berechnungslogik
	- Kann Berechnungen machen
	- Konkrete Hardware nicht relevant -> Black box
	- ![image5|325](14e5e1e98de247c995b507bf3b65776e.png)

- Schnittstelle zu SW - Instruction Set Architecture (ISA)
	- Liste aller Instruktionen
	    - Spezifiziert Anzahl Register, Größe, Verwendbarkeit Registerslots von jeder Operation
	- Datentypen (Byte, Word, Dword (32 bit), Qword (64 bit))
	- Betriebsmodi (32/64bit), hier x86-64

## Register (64 bit)
- Verwendet für die meisten Operationen
- Begrenzte Anzahl an Slots im Register
    - Wenn man mehr braucht -> Stack
- Namen von Felder
    - ax = 16 bit = ah + al = 2 \* 8 bit
	    - h - higher, l - lower
    - eax = 32 bit (extended)
    - rax = 64 bit (really extended)
- In x86-64
    - 16 general purpose register
    - Instruction pointer rip

## RAM
- Byte-weise adressierbar
- Enthält Programm Code & Daten
- Zugriff relativ langsam
	- Ist physikalisch weiter weg
- Ist ein fixed array

## X86-64 Assembler
- Standarisierung von Locations von bestimmten Werten damit man nicht immer alles durchsuchen muss
	- Rückgabewert in rax
	- Argumente in rdi, rsi
- Jeder Befehl hat andere Latenz
- Assembler code ist HW abhängig
	- Nutzt verfügbare HW features möglichst gut aus
- Assembler code -> Opcode (Maschienencode)

- ![image1|425](0fc2197c97a74b609d755342e1bd5bf1.png) 
	- Func ist Funktionsname

- ![image2|425](2f7b47fb41c641a488aba46e7b5bdc46.png)
	 - cmp compare
	 - jcc Jump when condition ``cc`` true
		 - e equal
		 - le less or equal
		 - g greater than
		 
	- Label enden mit ":"
		- Convention: Sprunglabel mit .L Benennen, sonst ununterscheidbar zu Funktionsnamen
		- Hier: .Lequal
		- Man kann auch zu Funktionen (also jedem Label) springen

# Speicherhierarchie
![image3|475](3a70ac4e57bd439890daa368f7a6b789.png)
- Keine Kontrolle über Caches <- macht CPU

# Einordnung Assembler
![image4|475](e8f1402a8bf1468aad26d6872c2ec83c.png)

# C-Compiler
### Proprecessor
- filaA.c (auf Linux muss .c nicht sein) -\> fileA.i)
- Setzt code aus Libraries ein
- Filtert code nach Ausführbarkeit auf HW
    - z.B. code kann/soll nur auf 512bit Prozessor ausgeführt werden

### C-Compiler
  - gcc -o fileA.s -S fileA.c
  - fileA.i -\> fileA.s
  - Code -\> Assembly

### Assembler
  - fileA.s -\> fileA.o

### Linker
  - fileA.o -\> exec

> Warum schreiben wir in Assembly statt C?
- Standard Compiler kann nur Optimierungen anhand Codestruktur machen, Mensch kann noch Micro-Optimierungen durchführen, weil er den Code versteht

> Wenn wir schon Assembly schreiben
- Es wird kein Compiler mehr gebraucht, da man schon in Assembler schon ist
- Nur Preprocessor