# CLAUDE.md — Fauteck-Fork von spoolman-mcp

Dieses Repo ist ein Fork von [Disane87/spoolman-mcp](https://github.com/Disane87/spoolman-mcp)
für Niklas' Homelab. **Upstream-README und Code bleiben unverändert**, damit Merges
von Upstream konfliktarm bleiben. Fauteck-spezifische Hinweise leben in dieser
Datei — sie existiert im Upstream nicht.

> Bis 2026-08-26 hieß diese Datei `FAUTECK.md`. Unter dem Namen hat Claude Code
> sie nie geladen: erkannt wird `CLAUDE.md` im Repository-Root. Die Regeln standen
> also da, ohne je zu wirken — genau die Sorte „Behauptung, die niemand prüft".

---

## Wissensquelle: llm-wiki (Todoteck)

Zentrale, gepflegte Wissensschicht für projektübergreifendes Wissen ist das
**Projekt `llm-wiki` in Todoteck** — erreichbar über den Todoteck-MCP-Server
(`mcp__Todoteck__*`) oder die Todoteck-Weboberfläche.

> Es gibt **kein** Wiki-Repository auf GitHub. Ein früheres Spiegel-Repo
> (`Fauteck/llm-wiki`) ist archiviert und irrelevant — nicht lesen, nicht
> verlinken, nicht pflegen. Diese Datei hat bis 2026-08-26 genau dorthin
> gezeigt, als letzte im Bestand.

Pflicht vor inhaltlichen Antworten:

1. Notiz **`_index`** lesen — Katalog aller Wiki-Seiten.
2. Mindestens die Repo-Übersicht öffnen: Notiz **`spoolman-mcp`**.
3. Für Inventar-Pflege (Marken, Lagerorte, Löschreihenfolge, SpoolmanDB-Abgleich):
   Notiz **`Claude-Anweisung: Spoolman / 3D-Druck`**.

Nach faktischen Änderungen mit Wissens-Charakter: betroffene Wiki-Notiz pflegen.
Spielregeln stehen in der Notiz **`_schema`** — insbesondere „eine Heimat pro Fakt".

Werkzeuge: `search` / `get_note` zum Lesen, `append_note` für reine Ergänzungen,
`update_note` nur für echte Korrekturen im Bestand, danach `sync_wikilinks` und
`lint_wiki`.

**Arbeitsteilung:** *Was* im Filament-Bestand gilt (Marken, Konventionen,
Abgleich mit SpoolmanDB), steht im Wiki. *Wie* der Server gebaut ist und welche
Werkzeuge er anbietet, steht in diesem Repo — `README.md` und der Code. Nicht
duplizieren, verlinken.

---

## Doku-Hygiene

Doku veraltet an drei Stellen, und alle drei sind Aussagen, die nichts
nachrechnet: die **Kopie** (eine abgeleitete Seite wiederholt einen Fakt, dessen
Heimat woanders liegt), die **Sollens-Regel** (ein Regelwerk behauptet eine
Praxis, die so nicht gelebt wird) und die **handgepflegte Aufzählung** (eine
Tabelle spiegelt eine Menge aus dem Code).

Verbindlich vor Doku-Änderungen und bei jedem Aufräum-Durchgang: Notiz
**„Behauptungen, die niemand prüft"** im Todoteck-Projekt `llm-wiki`.

Kurzfassung für dieses Repo:

- Eine Regel hier beschreibt, was **tatsächlich passiert**. Weicht sie von der
  Praxis ab, wird die Regel korrigiert — nicht die Praxis behauptet.
- Die Werkzeugliste des Servers wird **nicht** in Prosa geführt. Sie steht im
  Code und im Upstream-README; eine dritte Aufzählung wäre eine Kopie, die mit
  jedem neuen Tool ein Stück falscher wird.

---

## Release-Weg — die bewusste Abweichung von der Fauteck-Regel

Die übrigen Fauteck-Repos halten „kein SemVer, keine Git-Tags, Container-Tags
`latest` + SHA". **Hier gilt das nicht**, und das ist kein Versehen:

- Dies ist ein **npm-Paket**, kein Dienst. Ein npm-Paket ohne Version ist nicht
  installierbar; SemVer ist hier die Schnittstelle, nicht Zierrat.
- `.github/workflows/release.yml` läuft auf **Push nach `main`** und ruft
  `semantic-release`. Die Version fällt aus den Commit-Präfixen
  (`feat` → minor, `fix`/`perf`/`refactor` → patch, `docs`/`style`/`chore` → kein
  Release). Commit-Nachrichten sind hier also wirksam, nicht nur beschreibend.
- `.github/workflows/build.yml` baut das Container-Image und läuft **nur** auf
  `workflow_dispatch`.

**Kein automatisches Gate:** Weder Workflow führt Tests aus. Was geprüft werden
soll, wird vor dem Merge von Hand geprüft.
