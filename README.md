# ghostty

Config **Ghostty**, który wygląda jak mój [alacritty](https://github.com/K-u-r-c/alacritty): czarne tło, jasnoszary tekst, przezroczystość 0.95, paleta kolorów z domyślnego Alacritty. Na Hyprlandzie z rozmyciem wygląda to jak szkło. Bez paska tytułu, bez marginesów, kursor jako pełny blok bez mrugania.

Ghostty obsługuje protokół graficzny Kitty, więc obrazki w terminalu (np. wykresy z notebooków Jupytera w Neovimie) wyświetlają się w pełnej jakości.

- **Shift+Enter** nie ma własnego skrótu (w Alacritty wysyła `Esc`+`Enter`). Ghostty obsługuje protokół klawiatury Kitty, więc Claude Code sam robi nową linię, a Neovim dostaje prawdziwe `<S-CR>` (np. uruchomienie komórki w notebooku). W tmuxie potrzebne jest `extended-keys` (jest w moim [tmux](https://github.com/K-u-r-c/tmux)).
- Ghostty nie pyta sam o zamknięcie okna (`confirm-close-surface = false`). Robi to `killactive.sh` z [hypr](https://github.com/K-u-r-c/hypr) pod SUPER+W.
- Czcionka: Noto Sans Mono 11.25 pt (to samo, co systemowe `monospace` w Alacritty). Shell bierze się z `$SHELL`, u mnie to fish.

> Część zestawu **[linux-tools](https://github.com/K-u-r-c/linux-tools)**. Pasuje do [hypr](https://github.com/K-u-r-c/hypr) (SUPER+Enter), [tmux](https://github.com/K-u-r-c/tmux) i [nvim](https://github.com/K-u-r-c/nvim).

## Instalacja

```bash
sudo pacman -S --needed ghostty noto-fonts
[ -d ~/.config/ghostty ] && mv ~/.config/ghostty ~/.config/ghostty.bak
git clone https://github.com/K-u-r-c/ghostty ~/.config/ghostty
ghostty +validate-config
```

W tmuxie obrazki wymagają `set -g allow-passthrough on`.

Aktualizacja: `git -C ~/.config/ghostty pull`, potem w Ghostty Ctrl+Shift+, (przeładowanie configu).
