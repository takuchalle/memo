Omarchy のデフォルトシェルは `bash`なので、`zsh`に切り替える

```bash
sudo pacman -S zsh
which zsh
chsh /usr/bin/zsh # which zsh で表示されたパスを指定する
# 再起動する
```

Omarchy にはすでに便利ツールはインストールされているから設定を読み込む。必要に応じてPATHを設定する。

```.zshrc
if command -v mise &> /dev/null; then
  eval "$(mise activate zsh)"
fi

if command -v starship &> /dev/null; then
  eval "$(starship init zsh)"
fi

if command -v zoxide &> /dev/null; then
  eval "$(zoxide init zsh)"
fi

if command -v try &> /dev/null; then
  eval "$(try init ~/Work/tries)"
fi

if command -v fzf &> /dev/null; then
  if [[ -f /usr/share/fzf/completion.zsh ]]; then
    source /usr/share/fzf/completion.zsh
  fi
  if [[ -f /usr/share/fzf/key-bindings.zsh ]]; then
    source /usr/share/fzf/key-bindings.zsh
  fi
fi

export PATH=$PATH:~/.bun/bin
```

最新の`.zshrc`はここで管理してる。無駄に `chezmoi`を使ってる。

https://github.com/takuchalle/dotfiles-chezmoi/blob/main/dot_zshrc