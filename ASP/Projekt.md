
> [!important] Praktikumsordnung lesen
> https://asp.caps.in.tum.de/material/ASP_Praktikumsordnung.pdf
> Deadline: **1.2.2026 23:59 Uhr**

Projektphase
- Benotete Prüfungsleistung Projekt
- 3er Gruppen (mit Präferenzen)
- Implementierung + Kurzbericht (800 Wörter)
- Vorträge vsl. 9.3. - 13.3. Präsenz in Garching
	- termine brauchen extra anmeldung
	- first come first serve

- Bewertung durch automatische Tests + manueller Tutor
	- Gute Kommentare & commit messages 

----

Kurzbericht
- Probstellung, Lösungsansatz, Evaluierung der Ansätze, Ergebnisse analysieren
	- Evaluierung des Ansatzes und dessen Implementierung -> wie gut ist die? Vergleiche?
- 800 Wörter

Implementierung
- Mittel zum Zweck: notwendig zur Evaluierung
- Hauptimplementierung in Assembler
- Vergleichsimplentierungen -> Bonuspunkte
	- C
	- ssid/simd
- muss funktionieren auf ==lxhalle==

Vortrag
- Vorstellung 
	- Problemstellung (Beispiele)
	- Ansätze (Grafiken)
	- Ergebnisse (Benchmarking -> HW, Input,) 
		- nur Wichtiges
- auf relevante Inhalte fokussieren
- -> Handreichung zur Projektphase
- hard time limit 15min

Fragen
- warum diese Implementierung?
	- -> alle müssen gesamten code kennen
- zu Performanzergebnissen, Entscheidungen, mögliche Alternativen
	- auch vorstellbar: sachen die man nicht mehr geschafft hat aber durchaus machen könnte
- Details in Implementierung/Kurzbericht
- Zum Inhalt des Praktikums
	- tendenziell eher zu Konzepten

----

Mögl. Vorgehensweise Impl
- einfachen Ansatz in C 
	- noch nicht großartig auf Optimierung achten
	- vollständig fktfähiges (einfaches) Rahmenprogramm
	- -> erste Referenzimplementierung zum Testen von Korrektheit und Performanz

- Optimierte Ansätze auch erst in C implementieren
	- einfacher zu debuggen als Assembler

Optimierung
- Konzeptionelle Optimierungen wichtiger als Mikrooptimierung
- Assembler-Impl muss nicht besser als C-Impl sein
	- da compiler existiert
	- Wichtiger: Untershciede (korrekt) begründen -> im Kurzbericht und Präse

Implementierung Tipps
- Rahmenbedingungen beachten! 
	- Programmoptionen, Ein/Ausgabe genau wie vorgegeben implementieren
- (Sinnvolle) Code dokumentierungen
- Keine SegFaults
	- Randfälle in Nutzereingaben abfangen etc
	- Analysetools (Valgrind, perf, sanitiser)
- No over-engineering
- Sinvolle & hilfreiche Fehlermeldungen z.B. bei invalider Input
- Vorgegebenes git repo benutzen
	- master branch wird bewertet

Zeitplanung
- ggf Zeitplan erstellen
	- regelmäßige Fortschrittskontrollen
- Genug zeit für Kurzbericht und Vortrag einplanen
	- Zeit für Bericht, Vortrag, Doku ~ Zeit für Impl
- Alles zum selben deadline

