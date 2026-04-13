## 2.1 Definition
- **Alphabet** $\sum$ ist endliche Menge
- **Wort**/String über $\sum$ ist endliche Folge von Zeichen aus $\sum$
- $|\omega |$ bezeichnet die Länge des Wortes $\omega$
- das **leere Wort** (das einzige Wort der Länge 0) wird mit bezeichnet
- sind $u$ und $v$ Wörter, so ist $uv$ ihre **Konkatenation**
- ist $\omega$ ein Wort, so ist $\omega ^{n}$ definiert durch (n Wortlänge)
	- $\omega^{0}=e$, $\omega^n=\omega \omega^n$
- $\sum^*$ ist Menge aller Wörter über $\sum$
> Teilmenge $L \subseteq \sum^*$ ist **(formale) Sprache**
	- Leere Menge $\emptyset$ ist formale Sprache

## 2.3 Definition Operation auf Sprachen
Seien $A, B \subseteq \sum^*$

**Konkatenation**
$AB=\{ uv | u \in A \land v \in B \}$
Reihenfolge wichtig! 

$A^n=\{ \omega _{1}\dots \omega_{n} | \omega _{1}\dots \omega_{n} \in A \}$
- $A^{0}={e}$ und $A^{n+1}=AA^n$

$A^{*}=\{ \omega_{1}\dots \omega _{n} | n \geq 0 \land \omega_{1}\dots \omega_{n} \in A \}=\bigcup_{n \in N} A^n$
- ==enthält leeres Wort!==

$A^{+}= AA^{*}= \bigcup_{n\geq 1}A^n$
- Menge alle nicht-leeren Wörter

$\emptyset^{*}= \{ e \}$

## 2.4 Lemma
$\emptyset A = \emptyset$
- Konkatenation - u in leer kann nicht erfüllt werden deswegen ist leer

$\{ e \}A = A$

### 2.5 Lemma - Distributivgesetz
$A(B \cup C) = AB \cup AC$

$(A \cup B) C = AC \cup BC$

> $A(B \cap C) = AB \cap AC$ gilt nicht!

## 2.6 Lemma
$A^*A^{*}= A^*$

# 2.1 Grammatiken
## 2.7 Definition
Eine **Grammatik** ist ein 4-Tupel $G=\left\{  V, \sum, P, S  \right\}$, wobei 

V endliche Menge von **Nichtterminalzeichen** oder Nichtterminale oder **Variablen**

$\sum$ ist endliche Menge von **Terminalzeichen** oder **Terminale**, disjunkt von $V$, auch genannt ein **Alphabet**

$P \subseteq \left( V \cup \sum \right)^{+}\times \left( V \cup \sum \right)^{*}$ ist Menge von **Produktionen** 

$S \in V$ ist **Startsymbol**

### Konventionen

## 2.9 Definition
Grammatik G induziert eine **Ableitungsrelation** $\to_{G}$ auf wörtern über $V \cup \sum$
$$\alpha \to_{G}\alpha'$$
gdw es eine Regel $\beta\to \beta'$ in P und Wörter $\alpha_{1}, \alpha_{2}$ gibt, sd
$$\alpha = \alpha_{1}\beta \alpha_{2}$$ und 
$$\alpha' = \alpha_{1}\beta'\alpha_{2}$$
