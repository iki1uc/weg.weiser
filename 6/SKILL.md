---
name: html-system-bundler
description: "Bündelt und verbessert vorhandene HTML-Websites, lokale HTML-Module und Begleitdateien zu einem vollständig offline funktionierenden, geprüften Browser-System als ZIP. Verwenden für lokale Website-Pakete, modulare Dashboards, Reparatur defekter relativer Verweise, Offline-Migration externer Abhängigkeiten sowie optional für System-, Hardware-, Verbindungs-, Kartenhaus-, Registry- und Status-Dashboards mit lokalen Visualisierungen, Ablaufansicht, Terminal-Log, Speicherung und JSON-Export. Nicht für reine Neugestaltung ohne Ausgangsmaterial oder PDF-Zusammenführungen."
---

# HTML-System-Bündler

## Zweck

Erstellt aus vorhandenen Websites, Modulen und Assets ein eigenständiges Browser-Paket. Die Standardausgabe ist ohne Netzwerk nutzbar: ein lokaler Einstiegspunkt, funktionierende relative Verweise, mitgelieferte Abhängigkeiten und eine geprüfte ZIP-Datei.

Lies bei Dashboard- oder interaktiven Systemprojekten zusätzlich `references/offline_dashboard_patterns.md`. Bei einem ausdrücklich angeforderten Rechen- oder Formel-Dashboard lies außerdem `references/calculation_dashboard_patterns.md`. Beide Referenzen enthalten optionale UI- und Verhaltensmuster.

## Eingaben und Ergebnis

- **Eingaben:** HTML, CSS, JavaScript, lokale Bilder/Schriften/Medien, optional eine Online-Referenz und Begleitdokumente. Eine URL dient nur als visuelle oder inhaltliche Referenz, solange keine vollständigen Quelldateien verfügbar sind.
- **Ergebnis:** Ein ZIP mit genau einem obersten Projektordner, `index.html` als lokalem Einstiegspunkt und ausschließlich benötigten Dateien.

## Ablauf

1. Inventarisiere alle Eingaben: Dateityp, Größe, Rolle, vermutete Startseiten, lokale Referenzen und externe Netzwerk-Abhängigkeiten. Prüfe auch HTML, CSS und JavaScript auf URLs, Imports, Fonts, APIs, Module, Bilder und Navigation.
2. Lege eine klare Paketstruktur fest: `index.html`, `assets/` für lokal verfügbare Ressourcen und `modules/` für HTML-Teile. Bewahre funktionierende Inhalte und die bestehende Informationsarchitektur.
3. Stelle Offline-Fähigkeit her. Liefere jede tatsächlich verfügbare Abhängigkeit lokal mit und ersetze eindeutige externe Referenzen durch relative lokale Pfade. Entferne keine Funktion und ersetze keine fehlende externe Datei stillschweigend.
4. Falls der Nutzer eine vollständige Offline-Funktion verlangt, prüfe verbleibende Netzwerkzugriffe als Blocker: CDN-Skripte, Webfonts, dynamische Imports, Fetch/XHR/WebSocket, Remote-Bilder und externe Links. Ersetze nur dann durch lokale Ressourcen oder browserinterne Standardmittel, wenn Quelle und Verhalten eindeutig sind. Andernfalls frage nach der Originaldatei oder einer bestätigten Vereinfachung.
5. Repariere eindeutige, blockierende Verweise und Strukturfehler. Frage vor einer sichtbaren Neugestaltung, einem Funktionsumbau, dem Löschen von Dateien oder mehreren plausiblen Zielseiten nach.
6. Erzeuge eine lokale Modulübersicht nur, wenn kein brauchbarer Einstieg existiert oder eine Bündeloberfläche ausdrücklich verlangt ist. Für optionale Dashboard-Erweiterungen verwende nur die Muster, die zum vorhandenen Inhalt passen: Registry, Statuskarten, Ablauf-/Dominoansicht, Terminal-Log, Hardwareprofil, lokale Speicherung und JSON-Export.
7. Prüfe `index.html` und alle verlinkten lokalen Ziele statisch. Kontrolliere, dass keine externen Netzwerk-Abhängigkeiten, defekten relativen Pfade oder leeren Platzhalter im Offline-Paket verbleiben. Teste JavaScript statisch, wenn eine passende Laufzeit verfügbar ist.
8. Packe nur finale nutzbare Dateien. Schließe Caches, Logs, Zugangsdaten, Rohmaterial, ungenutzte Duplikate und temporäre Dateien aus.
9. Validiere das Archiv programmgesteuert: lesbar, nicht leer, erwartete Startseite vorhanden, lokaler Linkgraph vollständig. Liefere ausschließlich das finale ZIP.

## Offline-Standard

- Verwende keine CDN-Skripte, Online-Fonts, Remote-CSS, Remote-Bilder oder Remote-Module im finalen Paket.
- Bevorzuge Systemschriften oder lokale Schriftdateien; entferne Webfont-Imports, wenn keine lokale Lizenz-/Schriftdatei vorliegt.
- Verwende relative URLs für alle mitgelieferten Ressourcen.
- Lokale `localStorage`-Nutzung und clientseitiger JSON-Export sind offline geeignet. Netzwerkzugriffe, serverseitige APIs oder Authentifizierung sind es nicht.
- Externe Navigation darf als klar gekennzeichneter Online-Link bestehen bleiben, aber sie darf keine Kernfunktion des Offline-Systems sein.
- Eine reine Online-Referenz ohne Quellmaterial darf nicht als irreführende Offline-Kopie ausgegeben werden.

## Dashboard-Module (optional)

Wende diese Module nur an, wenn der Nutzer sie verlangt oder sie aus den vorhandenen Projektinhalten eindeutig folgen. Erfinde keine Systemlogik.

- **Registry/Grid:** Karten für vorhandene Module mit Titel, Status, Kurzbeschreibung, Tags und lokalem Öffnen.
- **Status- und Messansicht:** Kennzahlen, Zustände, Fortschrittsbalken sowie erklärbare Berechnungen mit direkt veränderbaren Parametern.
- **Ablaufansicht:** Sequenz oder Domino-Kette für eine bereits definierte Reihenfolge; mit Start, Einzelschritt, Reset und sichtbarem Zustand.
- **Terminal-Log:** Lokales Ereignisprotokoll für Aktionen und Statusänderungen; keine simulierten Systemzugriffe als reale Tatsachen darstellen.
- **Lokale Persistenz/Export:** Einstellungen und UI-Zustand in `localStorage`; JSON-Export über browserinterne APIs.
- **Hardware-/Systemprofil:** Lokale CPU-, RAM-, Speicher- oder Schnittstellenansicht aus bereitgestellten Daten, mit klarer Quellenlage, Einheiten und Grenzen.
- **Verbindungs-/Speicherfluss:** Lokale Topologieansicht für bestätigte Geräte, Ports, Speicherwege oder Modulbeziehungen, einschließlich klar beschriftetem Primär-, Fallback- und Backup-Pfad.
- **Kartenhaus-/Domino-Muster:** Visualisierte Hierarchie bereits vorhandener Module und Ordner mit bestätigter Reihenfolge, Einzelschritt, Reset, Struktur-Registry und unveränderten Originalinhalten.
- **Registry-/Control-Dashboard:** Lokale Modulkarten mit überprüften relativen Links, Statuschips, selektierter Detailansicht, kontrollierten UI-Aktionen, Ereignislog und Datenexport.
- **Lokale Scan-Aktionen:** Interaktive Hervorhebungen oder Ansichten zu bereits im Paket vorhandenen Daten; sie dürfen keine reale Hardwareabfrage, Diagnose oder Netzwerkaktivität vortäuschen.
- **Mapping-Tabelle:** Verknüpfungen zwischen vorhandenen Modulen, Datenpunkten und Bedeutungen; nur für bestätigte Beziehungen.
- **Zugänglichkeit:** Tastaturbedienbare Buttons, sichtbare Fokuszustände, verständliche Labels, responsive Layouts und ausreichender Kontrast.

## Regeln

- Erfinde keine Marken, Inhalte, Systemlogik oder externe Dateien.
- Bewahre Originalmaterial und Struktur, außer bei bestätigten Reparaturen oder Erweiterungen.
- Frage bei unklarer Startseite, fehlenden Kern-Abhängigkeiten, Löschvorschlägen oder wesentlichen Änderungen nach.
- Behaupte keine Browser-Sichtprüfung, wenn keine Browser-Engine verfügbar ist.
- Liefere keine Zwischenstände; das ZIP ist das alleinige Endartefakt.

## Fehlerbehandlung

- Ist eine Datei nicht lesbar oder kein HTML-Modul, ermittle ihren Typ und frage, ob sie beigelegt, konvertiert oder ausgeschlossen werden soll.
- Bei mehreren möglichen Zielen für einen defekten relativen Pfad frage nach; korrigiere nur eindeutige Pfade selbst.
- Bei fehlenden externen Ressourcen nenne den Blocker und biete an: Originaldatei nachreichen, die Funktion sichtbar vereinfachen oder den Online-Teil klar ausgrenzen.
- Schlägt die Archivprüfung fehl, behebe den Packaging-Fehler und validiere erneut. Liefere kein defektes Archiv.

## Lieferung

Prüfe vor Auslieferung, dass das ZIP existiert, nicht leer ist, `index.html` enthält und alle lokalen Module sowie Assets erreichbar sind. Weise knapp an: entpacken und `index.html` im Browser öffnen.
