# Fauteck-Fork — Hinweise

Dieser Repo ist ein Fork von [Disane87/spoolman-mcp](https://github.com/Disane87/spoolman-mcp) für Niklas' Homelab. Upstream-README und Code bleiben unverändert, damit Merges von Upstream konfliktarm sind. Fauteck-spezifische Hinweise leben in dieser Datei.

## Wissensquelle: llm-wiki (in Todoteck)

Zentrale, projektübergreifende Wissensschicht ist das **Todoteck-Projekt
`llm-wiki`**, erreichbar über den **Todoteck-MCP** (`search`, `get_note`,
`list_notes`, …). Es hat das frühere GitHub-Repo `Fauteck/llm-wiki`
**abgelöst** — Todoteck ist die einzige Heimat des Wikis.

Pflicht vor inhaltlichen Antworten:
1. Notiz `_index` im Projekt `llm-wiki` lesen (Katalog aller Seiten).
2. Diese Repo-Übersicht öffnen: Notiz **„spoolman-mcp"**.
3. Bei einschlägigen Themen die passende Notiz lesen: Notiz **„Claude-Anweisung: Spoolman / 3D-Druck"**.

Grundsatz „eine Heimat pro Fakt": code-gebundene Doku bleibt im Repo
(README, docs/*, ADRs); das Wiki verlinkt darauf, kopiert sie nicht.
Übergreifendes/abgeleitetes Wissen lebt als Notiz im `llm-wiki`-Projekt.
Nach faktischen Änderungen mit Wissens-Charakter: betroffene Wiki-Notiz
+ Notiz `_log` pflegen.

Zugriffswege auf dasselbe Wiki:
- **Claude Code (Web/lokal):** Todoteck-MCP.
- **Claude-Chat / mobil:** Todoteck-MCP-Connector.
