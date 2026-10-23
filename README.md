# Seminararbeit – LaTeX-Template (Hochschule Burgenland, Department IT)

LaTeX-Vorlage für die **Seminararbeit** (z.B. *Seminar Aktuelle Themen*) an der Hochschule Burgenland.
Sie basiert auf dem offiziellen [MSc-Thesis-Template (MCCE)](https://github.com/igo3r/mcce) und setzt die Formatvorgaben der Word-Vorlage `Vorlage_Seminararbeit V1_3.docx` um:

| Vorgabe (Word-Vorlage)                          | Umsetzung in LaTeX                                   |
| ----------------------------------------------- | ---------------------------------------------------- |
| A4, Ränder links/rechts 2,5 cm, oben 2,5 cm, unten 2 cm, Bundsteg 1 cm | `geometry`                    |
| Book Antiqua 12 pt, Zeilenabstand 16 pt, 6 pt Absatzabstand, Blocksatz | `mathpazo` (Palatino), `\linespread{1.1}`, `\parskip` |
| Überschriften 16 / 14 / 14 / 13 pt fett         | KOMA-Script `\addtokomafont`                          |
| Titel Tahoma 24 pt fett, Deckblatt 14 pt / 12 pt | Helvetica-Klon (`phv`)                               |
| Seitenzahl rechts in der Fußzeile (10 pt)       | `scrlayer-scrpage`                                    |
| Tabellen 10 pt, Kopfzeile 11 pt; Beschriftungen 10 pt links | `caption`, `\tabular`-Override                |
| Zitierweise APA (Autor, Jahr, Seite)            | `biblatex` mit `style=apa` + Biber                    |
| Max. 3 Gliederungsebenen (z.B. 3.3.1)           | `secnumdepth=3`, `tocdepth=2`                         |
| Fortlaufende Nummerierung „Abbildung 1“, „Tabelle 1“, „Formel 1“ | `\counterwithout`                    |

## Struktur

```
seminararbeit.tex                 Hauptdatei – hier Kapitel ein-/auskommentieren
00_A_preamble/seminar.tex         Pakete und Formatvorgaben
00_A_preamble/german.tex          Beschriftungen Deckblatt (alternativ english.tex)
00_B_data/yourData.tex            >>> EIGENE DATEN: Titel, Name, PKZ, Studiengang, Datum <<<
00_C_Front_Matter/titlepage.tex   Deckblatt
00_C_setup/setup.tex              hyperref / PDF-Metadaten
00_D_config/config.tex            Inhaltsverzeichnis
00_figures/                       Abbildungen (Logo)
01_chapters/00/00_abstract_de.tex Kurzfassung
01_chapters/01/...                1 Einleitung (1.1 Problemstellung, 1.2 Zielsetzung und wiss. Fragestellung)
01_chapters/02/02_fundamentals.tex        2 Grundlagen
01_chapters/03/03_stateOfKnowledge.tex    3 Stand des Wissens
01_chapters/04/04_summary.tex             4 Zusammenfassung
02_toc/01/bibliography.tex        5 Literatur
02_toc/02..05                     Abbildungs-, Tabellen-, Formelverzeichnis, Abkürzungen
99_Z_Back_Matter/appendix/        Anhang
references.bib                    Literaturdatenbank (BibLaTeX)
```

## Verwendung

1. `00_B_data/yourData.tex` ausfüllen (Titel, Name, Personenkennzeichen, Studiengang, Datum).
2. Kapitel in `01_chapters/` befüllen – Platzhaltertexte stammen aus der Word-Vorlage und sind zu ersetzen.
3. Literatur in `references.bib` pflegen (empfohlen: [Zotero](https://www.zotero.org) + [Better BibTeX](https://retorque.re/zotero-better-bibtex/)).
4. Zitieren mit `\parencite[S.~12]{key}` → *(Autor, Jahr, S. 12)* oder `\textcite{key}` → *Autor (Jahr)*.
5. Formelverzeichnis und Abkürzungen sind optional – bei Nichtbedarf die Zeilen in `seminararbeit.tex` auskommentieren.

## Kompilieren

Benötigt eine TeX-Distribution (TeX Live / MiKTeX / TinyTeX) mit `latexmk` und `biber`.

```bash
latexmk -pdf seminararbeit.tex
```

Die Ausgabe landet in `out/seminararbeit.pdf` (siehe `.latexmkrc`). Aufräumen mit `latexmk -C`.

### VS Code

Mit der Extension **LaTeX Workshop** wird beim Speichern automatisch gebaut (`.vscode/settings.json`).
**LTeX** liefert Rechtschreib-/Grammatikprüfung (`de-AT`).

### Overleaf

Projekt als ZIP hochladen, `seminararbeit.tex` als Hauptdatei setzen, Compiler *pdfLaTeX* – Biber wird automatisch ausgeführt.
