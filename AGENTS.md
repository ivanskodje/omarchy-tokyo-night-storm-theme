# omarchy-tokyo-night-storm-theme

- The README contains no hex values, image alt text included. Point the reader to `colors.toml`, the single source for the palette.
- The README prose is Ivan's. Read it fresh before touching it, add only what was asked (one line where possible), never re-add what he deleted, and leave his wording, line breaks and whitespace as they are.
- Local behavior is not install behavior. `~/.config/omarchy/themes/tokyo-night-storm` is a symlink to this repo, which Omarchy stages in full, while `omarchy theme install` drops any `*.lua`, the terminal configs, `vscode.json` and every symlink. Before claiming anything about a real install, reproduce it the way upstream's `test/shell.d/theme-staging-test.sh` does, from the repo root:

```bash
tmp=$(mktemp -d)
mkdir -p "$tmp/.config/omarchy/themes/tokyo-night-storm/.git" "$tmp/.local/state/omarchy/current"
cp -r ./* "$tmp/.config/omarchy/themes/tokyo-night-storm/"
HOME="$tmp" OMARCHY_PATH=/usr/share/omarchy PATH=/usr/share/omarchy/bin:$PATH \
  OMARCHY_THEME_HEADLESS=1 OMARCHY_THEME_SKIP_BACKGROUND=1 XDG_RUNTIME_DIR="$tmp" \
  bash /usr/share/omarchy/bin/omarchy-theme-set tokyo-night-storm 2>"$tmp/stderr"
[[ -s $tmp/stderr ]] && cat "$tmp/stderr"
```

Stderr must be empty.
