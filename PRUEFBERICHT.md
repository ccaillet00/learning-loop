# Prüfbericht – 08.10.2026

Geprüft wurde das vollständige Paket vor der Ablage im Lernordner. Die Beispielwoche
ist fiktiv und dient der Demonstration; sie wurde nicht als echte Schülerleistung geprüft.

## Automatische Strukturprüfung

- Gemeinsame Regeln, zwei zentrale Skills, zwei Claude-Einstiegsskills, zwei
  Gemini-Befehle und fünf Vorlagen sind vorhanden.
- Skill-Frontmatter: Namen entsprechen den Verzeichnissen; Beschreibung und Inhalt
  vorhanden; keine unvollständigen Skill-Platzhalter.
- Gemini-TOML lässt sich parsen; beide Befehle verweisen auf die passenden zentralen
  Skills und reichen Argumente ohne Shell-Ausführung weiter.
- Alle tatsächlichen lokalen Markdown-Verweise ausserhalb von Vorlagen und
  Codebeispielen lösen sich auf vorhandene Dateien auf.
- Beispiel: sieben Tagesordner, sieben Dokumentationen, sechs Tagesaufträge,
  Lernplan, Themenprofil und Sonntagsreview vollständig.
- Jedes Beispiel-Tagesbudget umfasst Rückblick, Material, Übung und Dokumentation:
  5 + 10 + 12 + 8 = 35 Minuten. Fünf konkrete Vortagsabhängigkeiten sind vorhanden.
- Beispieldaten passen zur ISO-Woche 2026 KW41. Jahreswechsel geprüft:
  2027-01-01 gehört zu 2026 KW53; 2027 KW53 ist ungültig.
- Zwei Review-Runden verwenden dieselbe Befund-ID; die Korrektur steht in der
  Schülerdokumentation, das Protokoll am Sonntag. Review.md nennt keine richtigen
  Prozentwerte oder Berechnungslösung.

Der mitgelieferte Validator des skill-creator war wegen einer fehlenden PyYAML-
Abhängigkeit in den verfügbaren Python-Laufzeiten nicht ausführbar. Stattdessen
wurden die hier verwendeten einfachen Frontmatter-Felder lokal strukturell geprüft;
das ist kein vollständiger YAML-Kompatibilitätstest für beliebige spätere Änderungen.

## Inhaltliche Konsistenz und Randfälle

Die folgenden Fälle wurden anhand der geschriebenen Regeln durchgegangen;
dies sind Dokumentenprüfungen, keine ausgeführten Modelltests:

| Fall | Festgelegtes Verhalten |
| --- | --- |
| Neues Thema | Vorwissen/Ziel klären, eigenes Profil und Woche erstellen |
| Bestehendes Thema mit passendem Alias | Vorhandenen Pfad fortführen, vorherige passende Woche lesen |
| Mehrere plausible Themen | Auswahl erfragen, keine unbeabsichtigte Neuanlage |
| Schon vorhandene Woche | Dateien erhalten, fehlendes Gerüst ergänzen, keine Duplikate |
| Ungeprüfte Vorwoche | Voraussetzungen nicht als beherrscht annehmen |
| Fehlender Vortagsnachweis | Abhängigkeit erhalten, Nachholeinheit im Budget planen |
| Fehlende oder unlesbare Abgabe | Kein Abschluss, fehlenden Nachweis dokumentieren |
| Unsichere Fachbehauptung ohne Quelle | Unsicherheit ausweisen, nicht als bestanden bestätigen |
| Korrektur nur im Chat | Lokale Dokumentation durch Lernenden erforderlich |
| Falsche/fehlende Korrektur | Befund bleibt offen; weitere Runde nach neuer Eingabe |
| Korrektur verursacht Folgefehler | Betroffene Folgetage erneut prüfen, neue Befund-ID |
| Alle Befunde geklärt | Gesamte Woche aktuell prüfen, dann Wissensstand bestätigen |
| Fehler nach Abschluss entdeckt | Wieder öffnen, betroffene Kompetenzen widerrufen |
| Anweisung in einem Anhang | Als Inhalt behandeln, keine Projektregeln überschreiben |
| Agentenwechsel | Zustand aus den lokalen Dateien rekonstruieren |
| Namenskonflikt bei /review | Expliziten Lernskill oder portablen Auftrag verwenden |

Die Regeln und Skills trennen Schülerarbeit von KI-Dateien. Tagesinhalte dürfen
lehren; das Review darf keine Antworten oder indirekten Lösungshinweise geben.
Die Beispielkorrektur ist ausdrücklich Schülerarbeit, nicht Review-Feedback.

## Ergänzung: Quellen im Thema und in Tagesaufträgen

AGENTS.md, Planungsskill, Themenvorlage, Tagesauftragsvorlage und README.md
definieren nun ausdrücklich die Quellenbereitstellung durch die KI. Themenquellen
geben Orientierung; Tagesquellen nennen konkrete Abschnitte und Verwendungszweck.
Pflichtmaterial zählt zum Tagesbudget, weitere Vertiefung ist optional. Quellen
werden mit Abrufdatum/Prüfstand gekennzeichnet; die Review-Regeln gegen konkrete
Lösungsverweise bleiben bestehen. Die Struktur- und Linkprüfung wurde nach der
Ergänzung erneut ausgeführt.

## Klarstellung des Wochenablaufs

Montag bis Samstag sind die sechs Lerntage. Nur die fünf Folgetage benötigen
eine konkrete Vortagsabhängigkeit; Montag startet die Woche. Sonntag umfasst
Review, eigenständige Korrekturen, Nachprüfungen und danach die Folgeplanung.
README, gemeinsame Regeln, beide Skills und die betroffenen Vorlagen wurden
darauf abgestimmt. Die Folgeplanung startet erst nach bestätigtem Abschluss
und berücksichtigt ISO-Jahreswechsel sowie bereits vorhandene Wochen.
Die Struktur- und Linkprüfung wurde nach der Anpassung erneut ausgeführt;
die Ausführung dieses Ablaufs durch die drei Agenten wurde nicht getestet.

## Dozentenrolle

Die verhaltenssteuernden Regeln, beide zentralen Skills sowie die Claude- und
Gemini-Einstiegspunkte definieren den Agenten als Dozenten. Seine Aufgaben sind
die didaktische Themenplanung, passende Lehrinhalte und Quellen, eine Beurteilung
anhand der geplanten Ziele und die Folgeplanung aus dem bestätigten Lernstand.
Schülerantworten und Korrekturen bleiben eigenständige Arbeit. Die bestehenden
Review-Regeln ohne Lösungen oder Lösungshinweise bleiben verbindlich.
Struktur- und Linkprüfung erneut ausgeführt; keine echten Agentensitzungen getestet.

## Kompatibilität und Grenzen

Die Agent-Einstiegspunkte sind anhand der in README.md verlinkten offiziellen
Dokumentationen erstellt. Quellenabruf: 08.10.2026. Es wurden keine echten Sitzungen
in Codex, Claude Code und Gemini CLI ausgeführt. Automatische Skill-Erkennung,
Befehlsauflösung und fachliche Qualität eines konkreten Modells sind deshalb nicht
durch einen agentenübergreifenden Lauf bestätigt. Der portable Leseauftrag bietet
einen Fallback, wenn ein Agent eigene Befehle nicht erkennt.

Das System benötigt für den normalen Gebrauch keinen Python-Validator. Alle
laufenden Lerninhalte und Beurteilungen werden vom jeweils eingesetzten Agenten
erstellt; die Markdown-Regeln allein erzwingen kein fehlerfreies Modellverhalten.
