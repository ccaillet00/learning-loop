---
name: plan-learning
description: Erstellt als Dozent anhand eines Lernthemas eine lokale Lernwoche mit aufeinander aufbauenden Tagesaufträgen, prüft Vorwissen und erstellt Themen- und Wochenordner. Verwenden für neue oder fortgesetzte Lernwochen.
---

# Lernwoche als Dozent planen

Übernimm die Dozentenrolle aus AGENTS.md. Leite aus dem Thema und dem Lernziel
eine nachvollziehbare didaktische Reihenfolge ab: notwendige Grundlagen,
Verständnisaufbau und eigenständige Anwendung. Formuliere pro Kapitel überprüfbare
Ziele und bereite verständliche Lehrinhalte, passende Quellen und Übungen vor.
Passe Tiefe und Schwierigkeit an das Vorwissen an. Die Planung soll den Lernenden
fachlich führen; die Bearbeitung und Dokumentation der Aufgaben bleiben seine Arbeit.

Lies AGENTS.md im Lernwurzelordner und die fünf Markdown-Dateien in Vorlagen/.
Der Nutzerauftrag bestimmt Thema, Ziel, Niveau und Woche; ein freier Satz genügt.
Dieser Skill wird auch nach dem bestätigten Sonntagsreview für die Folgeplanung
verwendet. Dabei die unmittelbar auf die geprüfte Woche folgende ISO-Woche
verwenden, soweit kein anderer Zeitraum vorgegeben ist.
Arbeite im Lernwurzelordner, unabhängig vom Verzeichnis der Skill-Datei.

## Thema und Ausgangslage erkennen
1. Ermittle die echten Themenordner nach AGENTS.md. Vergleiche Ordnernamen,
   Titel, Aliase und Ziele aus THEMA.md; ignoriere Grossschreibung, unterschiedliche
   Leerzeichen und Unicode-Normalisierung bei der Suche. Ähnliche Begriffe sind
   nur Kandidaten: „KI“ und „Machine Learning“ nicht automatisch gleichsetzen.
2. Einen eindeutigen passenden Bestand weiterführen. Bei mehreren plausiblen
   Treffern kurz zur Auswahl fragen, bevor neue Themen-/Wochenordner entstehen.
   Einen ausdrücklich verlangten separaten Schwerpunkt als neues Thema behandeln.
   Fehlt ein Thema im Auftrag und ist keines eindeutig aktiv, nach dem Thema fragen.
3. Bei Bestand THEMA.md, letzten zeitlich vorherigen Lernplan, Tagesdokumentationen
   und Review lesen; weitere Vorwochen gezielt lesen, soweit Wissensstand oder
   offene Befunde es erfordern. Eine spätere Woche nicht als Vorwissen verwenden.
   Abgeschlossene Reviews sind die Basis des bestätigten Standes. Offene Befunde
   und ungeprüfte Selbstauskünfte getrennt halten. Fehlendes Review nicht erfinden.
4. Bei neuem Thema das Lernziel und relevante Vorerfahrung aus dem Auftrag nutzen.
   Fehlen entscheidende Angaben, wenige gezielte Fragen stellen. Bei breitem Thema
   einen handhabbaren Einstieg vorschlagen. Keine unnötige Rückfrage zu Routinewahl.
   Benötigte Grundlagen mit kurzer Diagnose oder Selbstauskunft einschätzen.
   Unbestätigtes Vorwissen konservativ planen und explizit kennzeichnen.

## Woche und Inhalt festlegen
5. Explizite KW/Jahr oder Datum nach ISO-8601 auflösen, sonst die in AGENTS.md
   definierte Standardwoche nutzen. Montag- und Sonntagsdatum sichtbar nennen.
   Bei widersprüchlichen Angaben oder ungültiger KW nachfragen. Beispiel für
   Jahreswechsel: 2027-01-01 gehört zur Woche 2026 KW53, Beginn 2026-12-28.
6. Wochenziel in überprüfbare Teilziele zerlegen. Jeden Pflichtinhalt innerhalb
   von Montag bis Samstag einplanen. Grundlagen zuerst; bei zu grossem Umfang
   Ziel verkleinern oder auf Folgewoche verschieben, statt Tageslimit zu überziehen.
   Offene Wissenslücken zuerst bearbeiten. Bei noch ungeprüfter Vorwoche keine
   neuen Ziele auf ungeklärte Voraussetzung bauen; unabhängige Ziele sind möglich.
7. Pro Tag Auftrag.md mit konkretem Kapitel, Lernzielen, notwendigen Begriffen,
   genau abgegrenztem Material, eigenständiger Aufgabe und Dokumentationsauftrag
   schreiben. Material darf Lehrinhalt enthalten, aber keine Musterantworten auf
   die Tagesaufgabe. Nur Links ohne konkrete Lernstrecke reichen nicht.
   Budget z. B. 5 Min Rückblick + 10 Min Material + 12 Min Übung + 8 Min Dokumentation
   = 35 Min; einschliesslich erforderlicher Einrichtung höchstens 40 Min.
   Kostenlose, kurze Materialien bevorzugen; keine Pflichtanschaffung voraussetzen.
   Quellen dürfen im Themenprofil und im Tagesauftrag mitgegeben werden: In
   THEMA.md übergreifende Grundlagen und weiterführende Materialien sammeln; in
   Auftrag.md gezielt passende Quellen mit Titel, URL/relativem Pfad, relevantem
   Abschnitt, Verwendungszweck und Abrufdatum/Prüfstand eintragen. Pflichtmaterial
   in die Lernstrecke und ihr Budget integrieren; zusätzliche Vertiefung ausdrücklich
   als optional kennzeichnen. Vorhandene Quellen ergänzen statt ungefragt ersetzen.
   Wenn keine externe Quelle verfügbar/geprüft ist, dies offen ausweisen; selbst
   verfassten Lehrinhalt als solchen kennzeichnen, keine Quelle erfinden.
8. Dienstag–Samstag: benenne das konkrete Artefakt/Ergebnis des Vortags und wie es
   verwendet wird. Ergänze einen kurzen Rückblick darauf. Ein blosses „baut auf
   gestern auf“ ist keine Abhängigkeit. Fehlt das notwendige Ergebnis später,
   kleinere Ersatz-/Nachholeinheit innerhalb des Limits planen und Abhängigkeit
   erhalten; keine Antwort für den Lernenden ausfüllen. Montag braucht keinen
   Bezug zum Sonntag. Lernplan.md führt alle Teilziele und Prüfkriterien zusammen.

## Ordner sicher erstellen
9. Neues Thema: sprechenden, portablen Ordnernamen verwenden; keine Pfadtrennzeichen,
   Steuerzeichen, ../, absoluten Pfade oder reservierten Dateinamen aus dem Titel
   übernehmen. Bei Namenskollision auflösen. THEMA.md anhand der Vorlage erstellen.
   Bestehendes Thema im gleichen Ordner belassen, gegebenenfalls Metadaten ergänzen.
10. Existiert die Zielwoche, zuerst Inhalt prüfen. Einen fertigen Plan zurückgeben
statt duplizieren; nur fehlende Gerüstdateien ergänzen. Unfertige KI-Aufträge
im Rahmen des Auftrags vervollständigen. Bereits bearbeitete Aufträge und
Lernenden-Dateien nicht überschreiben. Gewünschte inhaltliche Neuplanung einer
bearbeiteten Woche vorher abklären; alten Plan erhalten.
11. Unter Thema/Woche <ISO-Jahr> KW<NN>/ Lernplan.md, sieben Tagesordner,
Montag–Samstag Auftrag.md und alle sieben Dokumentation.md anlegen.
Sonntag/Review.md mit Status „nicht begonnen“ erstellen. Jede Vorlage vollständig
mit Datum, Thema und Ziel personalisieren, Schülerantworten aber leer lassen.
Sichtbare Platzhalter ausschliesslich in Lernenden-Eingabefeldern verwenden.
12. Vor Abschluss prüfen: sechs Pflicht-Lerneinheiten, sieben Dokumentationen,
fünf konkrete Vortagsabhängigkeiten, korrekte Datumsfolge/ISO-KW, Zeitbudgets,
nötiges Vorwissen, Quellen und relative Links. Inhalt nicht als gelernt markieren.
THEMA.md erhält die geplante Woche, jedoch keine neuen bestätigten Kompetenzen.

Antworte mit Themenentscheidung (Bestand/neu), Zeitraum, Wochenziel, Dateiablage,
offenen Annahmen und Startschritt. Die KI erstellt den Plan und die Ordner jetzt;
sie bietet nicht nur an, sie später zu erstellen.
