# learning-loop

Ein lokales, Markdown-basiertes Lernsystem mit aufbauenden Wochenplänen,
eigener Lerndokumentation und iterativen Reviews. Du bestimmst das Thema;
ein KI-Agent strukturiert die Lernwoche und prüft deine Ergebnisse.

Montag bis Samstag lernst du in kurzen Einheiten von höchstens **40 Minuten pro Tag**.
Sonntag ist der Review- und Korrekturtag: Du lässt die Woche prüfen, korrigierst
Fehler selbst und lässt jede Korrektur erneut prüfen. Nach bestätigtem Abschluss
plant die KI anschliessend die nächste Lernwoche. Das Review gibt keine Lösungen
oder Lösungshinweise vor.

## Funktionen

- **Lernen von Montag bis Samstag:** Montag startet die Lernwoche; die folgenden Tage bauen jeweils auf dem Ergebnis des Vortags auf.
- **Sonntag abschliessen und vorausplanen:** Review, eigenständige Korrekturen, Nachprüfung und anschliessend Planung der nächsten Woche.
- **Berücksichtigtes Vorwissen:** Notwendige Grundlagen werden vor weiterführenden Inhalten eingeplant.
- **Automatische Ordnerverwaltung:** Neue Themen und Wochen werden angelegt; bestehende Themen werden fortgeführt.
- **Quellen zum Lernen:** Übergreifende Materialien im Themenprofil und passende Abschnitte in den Tagesaufgaben.
- **Eigene Dokumentation:** Markdown-Dateien mit relativen Links auf Bilder, PDFs, Tabellen oder andere Anhänge.
- **Iterative Prüfung:** Stabile Befund-IDs und protokollierte Nachprüfungen bis zum bestätigten Abschluss.
- **Agentenwechsel:** Pläne, Wissensstand und Review-Verlauf liegen in Dateien statt nur im Chat.

## Voraussetzungen

Ein eingerichteter lokaler KI-Agent mit Lese- und Schreibzugriff auf den Lernordner,
beispielsweise OpenAI Codex, Claude Code oder Gemini CLI. Für die Arbeit an der
Dokumentation genügt ein Markdown-Editor. Webzugriff wird benötigt, wenn der Agent
aktuelle Quellen recherchieren soll.

Das System besteht aus Anweisungen und Vorlagen. Es benötigt keine Datenbank,
keinen eigenen Server und keine zusätzliche Laufzeit. Die Agenten und ihre Konten
werden separat eingerichtet. Ein Chat ohne lokalen Dateizugriff kann die Ordner
nicht selbst verwalten.

## Installation

1. Dieses Repository klonen oder auf GitHub über **Code → Download ZIP** herunterladen und entpacken.
2. Den vollständigen Repository-Ordner als Projekt im KI-Agenten öffnen oder den Agenten dort starten.
3. Prüfen, dass `AGENTS.md`, `Vorlagen/` sowie die versteckten Ordner `.agents/`, `.claude/` und `.gemini/` vorhanden sind.
4. Mit einer Lernplanung starten. Die Befehle und der portable Fallback stehen unten.

Du kannst den Ordner lokal auch `Lernen` nennen. Entscheidend ist, dass `AGENTS.md`
direkt im geöffneten Projektordner liegt. Beim Einfügen in ein bestehendes Lernsystem
zuerst sichern und vorhandene Dateien vergleichen.

## Schnellstart

In Codex:

```text
$plan-learning Thema: Netzwerktechnik. Ziel: Heimnetzwerke verstehen.
Vorwissen: Anfänger. Plane die nächste Lernwoche und gib passende Quellen mit.
```

In Claude Code oder Gemini CLI:

```text
/plan-learning Thema: Netzwerktechnik. Ziel: Heimnetzwerke verstehen.
Vorwissen: Anfänger. Plane die nächste Lernwoche und gib passende Quellen mit.
```

Die KI erkennt, ob ein passendes Thema bereits existiert, berücksichtigt den
Wissensstand und erstellt den Wochenplan, Tagesaufträge und leere Dokumentationen.
Bei mehreren plausiblen Themen fragt sie nach deiner Auswahl.

Öffne danach `Montag/Auftrag.md` in der angelegten Woche. Bearbeite die Aufgabe und
halte deine eigene Erklärung und dein Ergebnis in `Montag/Dokumentation.md` fest.

## Agenten und Befehle

Die gemeinsamen Regeln stehen in [AGENTS.md](AGENTS.md). Die vollständigen
Workflows liegen zentral in den Skills
[plan-learning](.agents/skills/plan-learning/SKILL.md) und
[review](.agents/skills/review/SKILL.md). Die Claude- und Gemini-Dateien verweisen darauf.

| Agent | Einstiegspunkt | Planung | Lernreview |
| --- | --- | --- | --- |
| OpenAI Codex | `AGENTS.md` und `.agents/skills/` | `$plan-learning …` oder Skill auswählen | `$review …` oder Lernskill auswählen |
| Claude Code | `CLAUDE.md` und `.claude/skills/` | `/plan-learning …` | `/review …`, sofern der lokale Lernskill aufgerufen wird |
| Gemini CLI | `GEMINI.md` und `.gemini/commands/` | `/plan-learning …` | `/review …`, Projektbefehl prüfen |
| Andere lokale Agenten | Regeln und Skill ausdrücklich lesen lassen | Auftrag in natürlicher Sprache | Auftrag in natürlicher Sprache |

**In Codex ist `/review` ein Code-Review-Befehl.** Verwende hier `$review` oder
wähle ausdrücklich den Lernskill. Auch bei anderen Agenten können Namenskonflikte
auftreten. Die verfügbaren Auswahlmenüs und Befehle hängen von der Version ab.

Offizielle Dokumentation:
[Codex-Skills](https://learn.chatgpt.com/docs/build-skills),
[Claude-Code-Skills](https://code.claude.com/docs/en/skills),
[Gemini-Projektbefehle](https://geminicli.com/docs/cli/custom-commands/) und
[GEMINI.md](https://geminicli.com/docs/cli/gemini-md/).

### Portabler Fallback

Wenn der Agent einen Skill oder Befehl nicht erkennt, starte ihn im Projektordner
neu und prüfe die versteckten Dateien. Alternativ funktioniert ein ausdrücklicher
Leseauftrag ohne eigenes Befehlsmenü:

```text
Lies AGENTS.md und .agents/skills/plan-learning/SKILL.md vollständig.
Plane und erstelle eine Lernwoche zum Thema Netzwerktechnik.
Ich bin Anfänger und möchte die Grundlagen verstehen. Gib passende Quellen mit.
```

```text
Lies AGENTS.md und .agents/skills/review/SKILL.md vollständig.
Prüfe die Lerndokumentationen der zuletzt bearbeiteten Woche im Thema Netzwerktechnik,
einschliesslich der verlinkten Anhänge. Keine Lösungen oder Lösungshinweise.
```

## Ablauf einer Lernwoche

### 1. Planen

Du nennst Thema, Ziel und Vorerfahrung. Eine konkrete Woche kannst du ergänzen,
zum Beispiel `2026 KW42`. Ohne Wochenangabe plant die KI die nächste noch nicht
begonnene Montag–Sonntag-Woche; am Montag die aktuelle Woche. Sie nennt den Zeitraum
und ihre Annahmen. Vorhandene Wochen werden nicht stillschweigend verschoben oder
überschrieben.

Die Planung unterscheidet Selbsteinschätzung von durch Reviews bestätigtem Wissen.
Fehlende Grundlagen werden zuerst bearbeitet. Ein zu grosses Ziel wird verkleinert
oder auf mehrere Wochen verteilt.

### 2. Montag bis Samstag lernen und dokumentieren

Jeder Tagesauftrag enthält Lernziele, Material, eine eigenständige Aufgabe und
Zeit für die Dokumentation. Der Richtwert ist **35 Minuten**, das Maximum
**40 Minuten insgesamt**. Rückblick, Pflichtmaterial, Übungen, erforderliche
Einrichtung und Dokumentation zählen dazu.

Dienstag bis Samstag verwenden jeweils ein konkretes Ergebnis des Vortags.
Montag kann neu beginnen und berücksichtigt trotzdem den bisherigen Wissensstand.
Wenn du nicht fertig wirst, dokumentiere deinen Stand und bitte um Anpassung der
nächsten Einheit. Die KI füllt deine Antworten nicht für dich aus.

Anhänge bleiben im jeweiligen Tagesordner. Verlinke sie aus der Dokumentation,
beispielsweise mit `[Skizze](Skizze.png)` oder `[Berechnung](Berechnung.csv)`.
Ein Bezug zum Vortag kann `[Vortag](../Montag/Dokumentation.md)` lauten.

### 3. Quellen nutzen

`THEMA.md` sammelt allgemeine Grundlagen und weiterführende Materialien.
`Auftrag.md` nennt Quellen für das konkrete Kapitel mit Titel, URL oder relativem
Dateipfad, relevantem Abschnitt, Verwendungszweck und Abrufdatum beziehungsweise
Prüfstand.

Pflichtmaterial ist im Tagesbudget enthalten. Zusätzliche Vertiefung wird als
optional gekennzeichnet. Ohne Quellenzugriff muss die KI unbestätigte Verweise
und selbst verfasstes Material entsprechend ausweisen.

### 4. Sonntag: Review der Lernwoche

Schreibe deine Wochenreflexion in `Sonntag/Dokumentation.md` und starte das Review.
Plane für Vorbereitung und Reflexion 30–40 Minuten ein. Nachkorrekturen können
zusätzliche Zeit benötigen. Planung und Prüfung erfolgen auf deinen Aufruf;
es gibt keinen automatischen Kalenderjob. Ein Review kann auch nachgeholt werden.

Beispiel in Codex; ersetze Thema und Woche durch deine tatsächlich bearbeitete Woche:

```text
$review Netzwerktechnik, Woche 2026 KW42
```

Die KI prüft die aktuellen Dokumentationen und relevanten Anhänge gegen den Plan.
Sie protokolliert erfüllte Ziele, Prüfgrenzen und Befunde in `Sonntag/Review.md`.
Ein Befund darf etwa so aussehen:

> F001 – Freitag, Abschnitt Ergebnis: Die Prozentangabe ist mit den dokumentierten
> Daten nicht konsistent. Überprüfe deine Berechnung eigenständig.

Das Feedback enthält keine richtigen Ergebnisse, Ersatzformulierungen, Lösungswege,
leitenden Hinweise oder Links auf konkrete Aufgabenlösungen.

### 5. Sonntag: Selbst korrigieren und erneut prüfen lassen

Überarbeite die betroffene Datei selbst. Halte Befund-ID, geänderte Datei, Abschnitt
und Datum in `Sonntag/Dokumentation.md` fest. Rufe dann den Lernreview erneut auf:

```text
$review Netzwerktechnik, Woche 2026 KW42. F001 ist korrigiert.
Prüfe die aktuellen Dateien und die davon abhängigen Tagesergebnisse erneut.
```

Die KI hängt eine neue Prüfrunde an und bestätigt eine Korrektur erst nach Prüfung.
Ein blosses „korrigiert“ ohne lokalen Nachweis reicht nicht. Unveränderte oder
weiterhin fehlerhafte Antworten bleiben offen; neue Fehler erhalten neue IDs.

| Gesamtstatus | Bedeutung |
| --- | --- |
| nicht begonnen | Noch keine Prüfung ausgeführt |
| Korrektur erforderlich | Mindestens ein Fachfehler oder Widerspruch offen |
| Prüfung unvollständig | Nachweise fehlen, sind unlesbar oder fachlich ungesichert |
| Abgeschlossen | Alle Pflichtziele belegt, Dokumentationen vollständig und Befunde geklärt |

Erst nach einer aktuellen Gesamtprüfung wird der bestätigte Wissensstand in
`THEMA.md` aktualisiert. Später entdeckte Fehler öffnen die Woche erneut und
widerrufen die betroffenen Kompetenzbestätigungen.

### 6. Sonntag: Anschliessend die nächste Woche planen

Nach dem bestätigten Abschluss plant die KI im selben Ablauf die unmittelbar
folgende Montag–Samstag-Lernwoche mit dem nächsten Sonntag für Review, Korrektur
und Planung. Sie nutzt das bestehende Thema, den bestätigten Wissensstand und
dein Lernziel. Du brauchst dafür keinen separaten Planungsaufruf, sofern diese
Angaben eindeutig sind. Bleiben Befunde offen, werden zuerst die Korrekturen
und Nachprüfungen abgeschlossen; die Planung wird nicht als bereits erledigt
ausgewiesen. Fehlt eine entscheidende Zielangabe, fragt die KI gezielt danach.

Du kannst die Planung auch separat aufrufen, etwa für eine andere Woche:

```text
$plan-learning Setze Netzwerktechnik in der nächsten Lernwoche fort.
Nutze den bestätigten Wissensstand und die offenen Befunde der Vorwoche.
```

Die KI liest das bestehende Profil und die passende vorherige Woche. Offene oder
ungeprüfte Voraussetzungen gelten nicht als beherrscht. Bei Bedarf beginnt die
neue Woche mit dem Bearbeiten dieser Lücken.

## Ordnerstruktur

```text
learning-loop/
├── README.md
├── AGENTS.md
├── CLAUDE.md
├── GEMINI.md
├── PRUEFBERICHT.md
├── .agents/skills/
│   ├── plan-learning/SKILL.md
│   └── review/SKILL.md
├── .claude/skills/
│   ├── plan-learning/SKILL.md
│   └── review/SKILL.md
├── .gemini/commands/
│   ├── plan-learning.toml
│   └── review.toml
├── Vorlagen/
├── Beispiel/                     # fiktive Demonstration
└── <Thema>/                      # entsteht bei deiner ersten Planung
    ├── THEMA.md
    └── Woche <ISO-Jahr> KW<NN>/
        ├── Lernplan.md
        ├── Montag/ … Samstag/
        │   ├── Auftrag.md
        │   ├── Dokumentation.md
        │   └── weitere Dateien
        └── Sonntag/
            ├── Dokumentation.md
            └── Review.md
```

Wochen verwenden das ISO-Wochenjahr und eine zweistellige Kalenderwoche.
Beispiel: Der 1. Januar 2027 gehört zu `Woche 2026 KW53`.

| Datei | Verantwortlich | Inhalt |
| --- | --- | --- |
| `THEMA.md` | KI mit deinen Angaben | Profil, Quellen, bestätigter Wissensstand, Lücken und Wochenübersicht |
| `Lernplan.md` | KI | Wochenziel, Tagesübersicht, Abhängigkeiten und Prüfkriterien |
| `Auftrag.md` | KI | Tageskapitel, Quellen, Übung und Zeitbudget |
| `Dokumentation.md` | Du | Eigene Erklärungen, Bearbeitung, Ergebnisse, Belege und Korrekturen |
| `Review.md` | KI | Befunde, Prüfrunden, Nachprüfungen und Gesamtstatus |

### Vorlagen und Beispiel

Die fünf Vorlagen sind direkt im Repository enthalten:
[Themenprofil](Vorlagen/Thema.md), [Lernplan](Vorlagen/Lernplan.md),
[Tagesauftrag](Vorlagen/Tagesauftrag.md),
[Tagesdokumentation](Vorlagen/Tagesdokumentation.md) und
[Wochenreview](Vorlagen/Wochenreview.md).

Beim Anlegen ersetzt die KI `{{…}}` durch konkrete Metadaten. Deine Antwortfelder
bleiben leer. Die [fiktive Beispielwoche](Beispiel/README.md) zeigt ausgefüllte
Dokumentationen, eine eigenständige Korrektur und zwei Review-Runden.
Sie zählt nicht als echtes Lernthema oder als Nachweis deines Wissens.

## Eigene Lerninhalte und öffentliches Repository

Das öffentliche Repository stellt Regeln, Skills, Vorlagen und das fiktive Beispiel
bereit. Für deine persönlichen Lerninhalte kannst du eine separate lokale Kopie
oder ein privates Repository verwenden. Prüfe vor einem öffentlichen Commit,
welche eigenen Dokumentationen und Anhänge enthalten sind.

Gemeinsame Regeln werden in `AGENTS.md` gepflegt, die Workflows in `.agents/skills/`.
Die agentenspezifischen Einstiegspunkte verweisen auf diese Dateien.
Sichere deinen Lernordner vor grösseren Änderungen; relative Links bleiben beim
Verschieben des vollständigen Ordners erhalten.

## Prüfstand und Grenzen

Die Dateien und lokalen Verweise wurden auf Struktur und Konsistenz geprüft.
Der [Prüfbericht](PRUEFBERICHT.md) beschreibt die Prüfungen und Randfälle.
Die verlinkten Agentendokumentationen wurden am 08.10.2026 abgerufen.
Echte Sitzungen in allen drei Agenten wurden nicht ausgeführt; automatische
Erkennung und Befehlsauflösung hängen vom eingesetzten Agenten und seiner Version ab.

Die Markdown-Regeln erzwingen kein fehlerfreies Modellverhalten. KI-Reviews können
irren; unzugängliche Anhänge und ungesicherte Fachbehauptungen bleiben ungeprüft.
Ohne Webzugriff darf die KI aktuelle Quellen nicht als extern verifiziert ausgeben.

Die Dateien liegen lokal. Je nach Agent können gelesene Inhalte zur Verarbeitung
an dessen Anbieter übertragen werden. Das Repository enthält keinen eigenen
Offline-Modellbetrieb.
