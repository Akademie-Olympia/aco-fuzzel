# Installation

## Installieren

::::{tab-set}
:::{tab-item} Installer
```bash
curl -fsSL https://raw.githubusercontent.com/Akademie-Olympia/aco-arch-dotfiles/main/install.sh | bash -s -- fuzzel
```
:::
:::{tab-item} pacman
Wenn das Repository schon eingerichtet ist (`aco-arch-dotfiles` Installer):

```bash
sudo pacman -S aco-arch-dotfiles-fuzzel
aco install fuzzel
```
:::
::::

Der Installer prüft den Signierschlüssel, richtet das Pacman-Repository ein,
installiert `aco-arch-dotfiles-fuzzel` samt Abhängigkeiten und aktiviert die Konfiguration. Bestehende
Dateien werden vorher gesichert.

## Aktualisieren

```bash
sudo pacman -Syu        # oder: aco update
```

Neue Vorgaben werden mit deinen eigenen Änderungen zusammengeführt. Wo beides
abweicht, legt `aco` eine `.pacnew`-Datei neben deine Datei. Nach Änderungen die
Anwendung neu starten. Fuzzel liest die Datei bei jedem Start neu.

## Entfernen

```bash
aco deactivate fuzzel                 # stellt die gesicherten Einstellungen wieder her
sudo pacman -Rns aco-arch-dotfiles-fuzzel
```

`pacman` löscht niemals dein Home-Verzeichnis, Backups oder eigene Änderungen.

## Wo liegt was?

| Ort | Inhalt |
| --- | --- |
| `/usr/share/arch-dotfiles/fuzzel/` | Vorgaben des Pakets (von pacman verwaltet) |
| `~/.local/share/arch-dotfiles/config/fuzzel/` | Deine bearbeitbare Kopie – hier änderst du |
| `~/.config/fuzzel` → `fuzzel.ini` | Verknüpfung auf deine Kopie |

`aco path` zeigt das Verzeichnis deiner Kopien. Quellen und Paketrezept:
[`packaging/arch/PKGBUILD`](https://github.com/Akademie-Olympia/aco-fuzzel/blob/main/packaging/arch/PKGBUILD).
