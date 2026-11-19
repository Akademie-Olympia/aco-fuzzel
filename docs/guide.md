# Fuzzel als zentrales Menü

Fuzzel ist der Anwendungsstarter von ACO – und mehr: Er ist das **gemeinsame Menü** fast aller
Skripte der Umgebung. Dank `--dmenu` zeigt er jede Liste an, die ein Skript ihm gibt, mit Tippsuche,
Pfeiltasten und Enter. Deshalb sieht jedes Auswahlmenü im System gleich aus.

## Wo Fuzzel überall steckt

| Aufruf | Taste | Zweck |
| --- | --- | --- |
| `fuzzel` | {kbd}`Super + Leertaste`, {kbd}`Alt + Leertaste`, {kbd}`Super + D` | Programme starten |
| `windowswitcher.sh` | {kbd}`Super + G` | Fenster über alle Monitore und Workspaces |
| `powermenu.sh` | {kbd}`Super + Esc` | Herunterfahren, Neustart, Standby, Sperren |
| `wallpaper.sh tui` | {kbd}`Super + Shift + W` | Hintergrundbild wählen |
| `monitors.sh menu` | {kbd}`Super + Shift + D` | Bildschirm-Layout |
| `aco keys --menu` | {kbd}`Super + K` | Alle Tastenkürzel durchsuchen |

Ein zweiter Druck auf die Taste schließt das Menü (`pkill -x fuzzel`).

## Bedienung

Einfach tippen – die Suche findet Name, Beschreibung, Kategorie und Befehl (`fields=name,generic,comment,categories,keywords,exec,filename`).
{kbd}`↑`/{kbd}`↓` oder {kbd}`Strg + P`/{kbd}`Strg + N` wählen, {kbd}`Enter` startet, {kbd}`Esc` bricht ab.
Das Menü schließt sich auch, sobald es den Fokus verliert.

## Was dieses Paket festlegt

| Einstellung | Wert | Wirkung |
| --- | --- | --- |
| `terminal` | `kitty -e` | Programme mit „Im Terminal starten" öffnen in Kitty |
| `width` / `lines` | 44 / 10 | Breite in Zeichen, sichtbare Zeilen |
| `layer` | `overlay` | Liegt über Vollbildfenstern |
| `match-counter` | an | Zeigt die Trefferzahl |
| `icons-enabled` | an (Adwaita) | Anwendungssymbole |
| `border` | 1 px, Akzentfarbe | `radius=0` – eckig, passend zu Waybar und Terminal |

## Eigene Menüs bauen

```bash
choice=$(printf 'Eins\nZwei\nDrei\n' | fuzzel --dmenu --prompt 'Wahl: ')
echo "$choice"
```

Nützliche Optionen: `--lines N`, `--width N`, `--anchor top-right`, `--hide-prompt`, `--index` (gibt die Nummer statt Text aus).
Ein Beispiel für ein Menü mit eigener Position ist `powermenu.sh` im Hyprland-Paket.

## Fehlersuche

- **Ändert sich nichts nach dem Bearbeiten?** Fuzzel liest die Datei bei jedem Start neu; bei Syntaxfehlern meldet `fuzzel` den Grund im Terminal.
- **Symbole fehlen:** Das Paket `adwaita-icon-theme` muss installiert sein.
- **Schrift ohne Symbole:** `ttf-jetbrains-mono-nerd` fehlt.

## Farbpalette (Catppuccin Mocha)

Alle Komponenten nutzen dieselben Farben, damit Terminal, Launcher, Dateimanager und Dialoge zusammenpassen:

| Rolle | Farbe | Verwendung |
| --- | --- | --- |
| Hintergrund | `#1e1e2e` | Fenster, Terminal |
| Tiefer Hintergrund | `#181825` | Leisten, Listen, Seitenleisten |
| Fläche | `#313244` | Eingabefelder, Buttons, Auswahl |
| Text | `#cdd6f4` | Schrift |
| Akzent | `#89b4fa` | Fokus, Rahmen, Auswahl |
| Treffer | `#94e2d5` | Suchtreffer |

## Anpassen und zurücksetzen

`~/.config/fuzzel` ist ein Link auf deine bearbeitbare Kopie unter
`~/.local/share/arch-dotfiles/config/fuzzel/`. Dort kannst du alles ändern; `pacman -Syu` überschreibt
deine Änderungen **nicht**. Bringt ein Update neue Vorgaben mit, landen sie als `.pacnew`-Datei neben deiner
Version, und du übernimmst, was du willst (`aco sync` führt zusammen, `aco status` zeigt den Zustand).
Zurück zu den Vorgaben: `aco deactivate fuzzel` stellt die früheren Einstellungen wieder her,
`aco install fuzzel` aktiviert die Paketvorgaben erneut.
