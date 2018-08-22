# 99 EndkontrolleUndAbgabe
Created Mittwoch 27 Juli 2016

Übersicht von allem, was getan werden muss
------------------------------------------

* ☐ TODO: Regex checks


| *Was ist zu tun?*                                                                                                  | *Tipp für die Vorgehensweise*                                                                                             |
|:-------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------|
| 01 - **Abbildungen**                                                                                               |                                                                                                                           |
| 01.1 - Die Tilde steht zwischen ``Abbildung`` und ``\ref{}``  (``Abbildung~\ref{}``)                               | STRG+F nach "Abbildung " ==> sollte nie so stehen.                                                                        |
| 01.2 - Einheiten in Diagrammen NICHT in eckigen Klammern sondern entweder                                          |                                                                                                                           |
| 01.6 - In jeder Caption muss ein Satzpunkt stehen                                                                  |                                                                                                                           |
| 01.3 - alle Bilder gut lesbar und sauber auch beim Druck!                                                          | Mache einen Testdruck deiner Abbildungen. Besonders bei dunklen Bilder problematisch                                      |
| 01.4 - alle Bilder mit Quellenangaben versehen.                                                                    | Der Reihe nach alle Bilder durchgehen                                                                                     |
| 01.5                                                                                                               |                                                                                                                           |
| 02 - **Gleichungen**                                                                                               |                                                                                                                           |
| 02.1 - alle Formeln sind nummeriert                                                                                |                                                                                                                           |
| 02.1 - auf alle Formeln wird durch (NUMMER) verwiesen (es wird ``~\eqref`` verwendet)                              | STRG+F nach "ref{" und beachte, wann es genutzt wird.                                                                     |
| 02.2 - Differenziationsoperator gerade gesetzt (nicht kursiv) - insbesondere bei Ableitungen und Integralen prüfen | Alle Gleichungen durchgehen. Verwenden den _\dd_ Befehl aus der Vorlage.                                                  |
| 02.3                                                                                                               |                                                                                                                           |
| 03 - **Sprachliche Korrektheit **                                                                                  |                                                                                                                           |
| 03.1 - Für gleiche Fachbegriffe wird stets die gleiche Schreibweise verwendet                                      | STRG+F nach den Schreibweisen und ersetzen.                                                                               |
| 03.2 - in deutschen Texten ausschließlich deutsche Kommas in Zahlen ``1,234``                                      | Regex Suche. "\d+[.]\d+" für englische Schreibweise (sollte nicht vorhanden sein). "\d+[,]\d+" für deutsche Schreibweise. |
| 03.3 - keine Rechtschreibfehler                                                                                    | copy & paste in Word                                                                                                      |
| 03.4 - verwende kein "man", "ich", "mein", "brauchbar", "meiste"                                                   | STRG+F nach " man" (für Suche im Satz) und STRG+F nach "Man " für Satzanfang. Analog die anderen Begriffe                 |
| 03.5 - Abkürzungen aus mehreren Wörtern mit ``\,`` - so wie bei ``z.\,B.``                                         |                                                                                                                           |
| 03.6 - alle Abkürzung vor der ersten Verwendung eingeführt                                                         | STRG+F nach der Abkürzung und bis zur ersten Verwendung gehen. Dann prüfen.                                               |
| 03.7                                                                                                               |                                                                                                                           |
| 04  - **Tabellen**                                                                                                 |                                                                                                                           |
| 04.1 - in Tabellen Zahlen mit gleichem Bezug mit gleicher Anzahl an Nachkommastellen                               | alle Tabellen durchgehen. Am besten jemand anderen drüberschauen lassen.                                                  |
| 04.2                                                                                                               |                                                                                                                           |
| 05 - **Zahlen mit und ohne Einheiten**                                                                             |                                                                                                                           |
| 05.1 - Einheiten gerade (nicht kursiv) gesetzt (mit siunitx Paket) ``\si{1,234}{\watt}``                           | Latex-Vorlage besitzt siunitx - Packet. also immer \si{1,234} {\watt} verwenden                                           |
| 05.2 - Zahlen OHNE Einheit mit ``/\ num{}``                                                                        | Regex Suche nach "\d+" (1 oder mehr digits). Dann jeweils überprüfen.                                                     |
| 05.3 - Zahlenwerte und Quellcodeteile im Text durch entsprechende Formatierung hervorgehoben.                      | Zahlen mit \si oder \ num, Quellcode durch \verb∣∣                                                                    |
| 08 - **Sonstiges**                                                                                                 |                                                                                                                           |
| 08.1 - alle Indizes, die keine Variablen sind, sondern eine Namensgebung darstellen gerade gesetzt                 | Beispiel k\mathrm{gerade}.  verwenden die Schriftart *\mathrm*                                                            |
| 08.2 - keine Overfull boxes                                                                                        | verwende \overfullrule = 2mm im ``diplom.tex`` um die Overful boxes anzuzeigen.                                           |


### Automatisierte Regex-Checks


* diese Regex-Checks sollten fehlerfrei durchlaufen

 

* ☐ TODO



### Overfull boxes erkennen
Mit dieser Zeile Code im root- document (diplom.tex) lassen sich overful boxes erkennen.
	\overfullrule = 2mm


![](./99_EndkontrolleUndAbgabe/pasted_image.png) 

Oft lieg es an folgenden Dingen:

* Das Wort ist unbekannt und kann desshalb nicht richtig getrennt werden (FlipFlop)
* ☐ TODO





